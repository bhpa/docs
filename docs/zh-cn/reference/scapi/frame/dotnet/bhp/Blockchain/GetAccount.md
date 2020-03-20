# Blockchain.GetAccount 方法 (byte[])

根据合约脚本的散列来获得一个账户（地址）。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern Bhp.SmartContract.Framework.Services.Bhp.Account GetAccount(byte[] script_hash)
```

参数：脚本散列，20 字节的字节数组。

返回值：账户，[Account](../Account.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] scriptHash = { 130,38,197,19,226,170,113,127,47,50,211,197,251,43,203,73,42,207,195,220 };
        Account acc = Blockchain.GetAccount(scriptHash);
    }
}
```

其中 script hash 可以在外部事先获得，也可以作为参数传入智能合约。下面是在外部代码中调用 SDK 将地址转成 script hash。

```c#
static void Main(string[] args)
{
    byte[] scriptHash = Bhp.Wallets.Wallet.ToScriptHash("ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY").ToArray();
}
```



[返回上级](../Blockchain.md)