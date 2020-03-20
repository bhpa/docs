# Blockchain.GetHeader 方法 (byte[])

通过区块 hash ，查找区块头。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern Bhp.SmartContract.Framework.Services.Bhp.Header GetHeader(byte[] hash)
```

参数：区块 Hash，32 字节的字节数组。

返回值：区块头，[Header](../Header.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] Header = new byte[] { 215,215,67,180,42,144,167,24,63,239,78,204,3,32,93,111,43,27,128,30,112,206,29,19,23,47,2,153,127,227,133,76 };
        Header bl = Blockchain.GetHeader(Header);
    }
}
```



[返回上级](../Blockchain.md)