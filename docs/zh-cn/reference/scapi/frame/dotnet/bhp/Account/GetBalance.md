# Account.GetBalance 方法 (byte[])

通过资产ID获得该账户中这种资产的余额。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public extern long GetBalance(byte[] asset_id)
```

参数：资产ID，即注册资产时的 RegistTransaction 的交易ID，32字节的byte数组。

返回值：账户中该资产余额，长整形，等于实际金额 × 10⁸。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] scriptHash = { 130,38,197,19,226,170,113,127,47,50,211,197,251,43,203,73,42,207,195,220 };
        Account account = Blockchain.GetAccount(scriptHash);
        //以BHP资产为例
        byte[] asset = { 84,168,10,76,114,246,21,122,122,240,167,83,252,74,196,175,107,21,154,23,99,77,213,127,236,243,25,254,171,111,247,19 };
        long balance = account.GetBalance(asset);
    }
}
```



[返回上级](../Account.md)