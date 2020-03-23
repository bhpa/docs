# 开发示例合约

我们已经搭建私链并启动节点连接私链，下文将以使用 windows 10 和 C# 为例，带领开发者配置环境、编写、编译以及在私链上部署和调用 BHP 智能合约。

在本节我们将完成以下任务：

- 安装合约开发环境
- 创建一个 BRC20 合约项目
- 编译合约

## 安装开发环境

### 安装 Visual Studio 2019

下载 [Visual Studio 2019](https://visualstudio.microsoft.com/zh-hans/thank-you-downloading-visual-studio/?sku=Community&rel=16) 并安装，注意安装时需要勾选 `.NET Core 跨平台开发` 。

![develop](../../assets/develop.png)

### 安装 BhpContractPlugin 插件

打开 Visual Studio 2019，点击 `工具` -> `扩展和更新` ，在左侧点击 `联机` ，搜索 BHP，安装 BhpContractPlugin 插件（该过程需要联网）。

### 配置编译器

1. 在 Github 上下载 [bhp-compiler](https://github.com/BhpAlpha/bhp-compiler) 项目到本地。

2. 在 Visual Studio 2019 上点击 `文件` -> `打开` -> `项目/解决方案`，选择项目文件中的 bhp-compiler.sln

3. 右键单击列表中的 bhpn 项目，点击 `发布`。

4. 配置好发布路径后，点击 `发布`。

   发布成功后，会在 bin\Release\netcoreapp2.0\publish 目录下生成 bhp.exe 文件。


### 设置环境变量

接下来需要添加 path，让任何位置都能访问 bhp.exe。方法如下：

1. 在 Windows10 上 按 Windows + S 键，输入环境变量，选择 `编辑账户的环境变量` 

2. 选择 Path, 点击 `编辑`

3. 在弹出来的窗口中点击 `新建` 并输入你自己的 bhpn.exe 所在的文件夹目录，点击 `确定` 。

   ![develop2](../../assets/develop2.png)

> [!Note]
>
> 在环境变量中不要添加 “…… neon.exe” 字样的路径，要填写 bhpn.exe **所在的文件夹目录** 而非 bhpn.exe 本身的路径。

添加完 path 后，运行 CMD 或者 PowerShell 测试一下（如果添加 path 前就已经启动了 CMD 则要关掉重启），输入 bhpn 后，没有报错，如图所示输出版本号的提示信息即表示环境变量配置成功。

![develop3](../../assets/develop3.png)

## 创建 BHP 合约项目

完成以上步骤后，即可在 Visual Studio 2019 中创建 NEO 智能合约项目（.NET Framework 版本任意）：

1. 点击 `文件` -> `新建` -> `项目`。
2. 在列表中选择 `BhpContract` 并进行必要设置后，点击 `确定`。

![develop4](../../assets/develop4.png)

创建项目后，会自动生成一个 C# 文件，默认的类继承于 SmartContract，如图，此刻你已经拥有一个 Hello World 了！

![develop5](../../assets/develop5.png)

当然这只是一个简单的向私有化存储区中以 key-value 方式存储数据的操作。

## 编辑 BRC20 代码

很多开发者比较关心的是如何在 BHP 公链上发布自己的合约资产，现在我们就在私链上一步步实现。

1. 从 [Github](https://github.com/BhpAlpha/examples)上下载 BRC20 示例。

2. 在 Visual Studio 2019 中创建一个 BHP 智能合约项目，这里命名为 Brc20Contract。

3. 打开示例文件 Brc20Contract.cs

   代码中主要写了资产的基本信息和供调用的方法，你可以根据自己的需要增删或修改。

4. 这里我们对示例文件进行一些修改：

   - 设定资产总值和`deploy` 方法
   - 将 "Owner" 替换成钱包 0.json 中的地址 （否则将无法使用钱包中的资产）

   代码如下：

```c#
using Bhp.SmartContract.Framework;
using Bhp.SmartContract.Framework.Services.Bhp;
using Bhp.SmartContract.Framework.Services.System;
using System;
using System.ComponentModel;
using System.Numerics;

namespace Brc20Contract
{
    public class Brc20Contract : SmartContract
    {
        [DisplayName("transfer")]
        public static event Action<byte[], byte[], BigInteger> Transferred;

        private static readonly byte[] Owner = "AXo6nRuiFxLqS9XnYS8x1f25eM5mGxkAq7".ToScriptHash(); //Owner Address
        private static readonly BigInteger TotalSupplyValue = 10000000000000000;//总资产

        public static object Main(string method, object[] args)
        {
            if (Runtime.Trigger == TriggerType.Verification)
            {
                return Runtime.CheckWitness(Owner);
            }
            else if (Runtime.Trigger == TriggerType.Application)
            {
                var callscript = ExecutionEngine.CallingScriptHash;

                if (method == "totalSupply") return TotalSupply();

                if (method == "name") return Name();

                if (method == "symbol") return Symbol();

                if (method == "decimals") return Decimals();

                if (method == "balanceOf") return BalanceOf((byte[])args[0]);

                if (method == "transfer") return Transfer((byte[])args[0], (byte[])args[1], (BigInteger)args[2], callscript);

                if (method == "deploy") return Deploy();

                if (method == "supportedStandards") return SupportedStandards();
            }
            return false;
        }

        [DisplayName("totalSupply")]
        public static BigInteger TotalSupply()
        {
            StorageMap contract = Storage.CurrentContext.CreateMap(nameof(contract));
            return contract.Get("totalSupply").AsBigInteger();
        }

        [DisplayName("name")]
        public static string Name() => "MyBRC20";

        [DisplayName("symbol")]
        public static string Symbol() => "MYB";

        [DisplayName("decimals")]
        public static byte Decimals() => 8;

        [DisplayName("balanceOf")]
        public static BigInteger BalanceOf(byte[] account)
        {
            if (account.Length != 20)
                throw new InvalidOperationException("The parameter account SHOULD be 20-byte addresses.");
            StorageMap asset = Storage.CurrentContext.CreateMap(nameof(asset));
            return asset.Get(account).AsBigInteger();
        }

#if DEBUG
        [DisplayName("transfer")] //Only for ABI file
        public static bool Transfer(byte[] from, byte[] to, BigInteger amount) => true;
#endif
        //Methods of actual execution
        private static bool Transfer(byte[] from, byte[] to, BigInteger amount, byte[] callscript)
        {
            //Check parameters
            if (from.Length != 20 || to.Length != 20)
                throw new InvalidOperationException("The parameters from and to SHOULD be 20-byte addresses.");
            if (amount <= 0)
                throw new InvalidOperationException("The parameter amount MUST be greater than 0.");
            if (!IsPayable(to))
                return false;
            if (!Runtime.CheckWitness(from) && from.AsBigInteger() != callscript.AsBigInteger())
                return false;
            StorageMap asset = Storage.CurrentContext.CreateMap(nameof(asset));
            var fromAmount = asset.Get(from).AsBigInteger();
            if (fromAmount < amount)
                return false;
            if (from == to)
                return true;

            //Reduce payer balances
            if (fromAmount == amount)
                asset.Delete(from);
            else
                asset.Put(from, fromAmount - amount);

            //Increase the payee balance
            var toAmount = asset.Get(to).AsBigInteger();
            asset.Put(to, toAmount + amount);

            Transferred(from, to, amount);
            return true;
        }

        [DisplayName("deploy")]
        public static bool Deploy()
        {
            if (TotalSupply() != 0) return false;
            StorageMap contract = Storage.CurrentContext.CreateMap(nameof(contract));
            contract.Put("totalSupply", TotalSupplyValue);
            StorageMap asset = Storage.CurrentContext.CreateMap(nameof(asset));
            asset.Put(Owner, TotalSupplyValue);
            Transferred(null, Owner, TotalSupplyValue);
            return true;
        }

        [DisplayName("supportedStandards")]
        public static string[] SupportedStandards() => new string[] { "BRC-20" };

        private static bool IsPayable(byte[] to)
        {
            var c = Blockchain.GetContract(to);
            return c == null || c.IsPayable;
        }

    }
}
```

编辑完之后，我们已经完成了一份智能合约的代码部分。

## 编译合约文件

点击菜单栏上的 `生成`->`生成解决方案`（快捷键 Ctrl + Shift + B）开始编译程序。

编译成功后你会在该项目的 `bin/Debug` 目录下看到生成的 `Brc20Contract.avm` 文件，该文件即是生成的 BHP 智能合约文件。

`Brc20Contract.abi.json` 是智能合约的描述文档，文档中对合约的 ScriptHash、入口、方法、参数、返回值等进行了描述。

## 继续阅读

[部署与调用合约](deploy.md)

