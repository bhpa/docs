# Runtime.CheckWitness 方法 (byte[])

验证调用该智能合约的交易/区块是否验证过所需的脚本散列。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern bool CheckWitness(byte[] hashOrPubkey)
```

参数：

hashOrPubkey：脚本散列或者是公钥，byte 数组类型。其中脚本散列为 20 字节，公钥为 33 字节。

返回值：调用该智能合约的交易/区块是否验证过所需的脚本散列，bool 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] pubKey = { 3,133,91,111,15,116,128,114,208,206,218,240,72,231,208,214,204,76,231,5,217,231,148,12,191,41,14,89,253,94,193,58,164 };
        bool result = Runtime.CheckWitness(pubKey);
        //byte[] scriptHash = { 130,38,197,19,226,170,113,127,47,50,211,197,251,43,203,73,42,207,195,220 };
        //bool result = Runtime.CheckWitness(scriptHash);
    }
}
```



[返回上级](../Runtime.md)