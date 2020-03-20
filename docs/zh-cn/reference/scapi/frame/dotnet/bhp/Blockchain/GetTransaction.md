# Blockchain.GetTransaction 方法 (byte[])

通过交易 ID 查找交易。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern Bhp.SmartContract.Framework.Services.Bhp.Transaction GetTransaction(byte[] hash)
```

参数：交易ID（交易散列），32字节的字节数组。

返回值：交易，[Transaction](../Transaction.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] transaction = new byte[] { 115,96,59,84,98,14,63,134,141,6,185,214,139,61,142,84,11,133,151,93,155,238,35,4,58,1,27,183,33,185,60,238 };
        Transaction tx = Blockchain.GetTransaction(transaction);
    }
}
```



[返回上级](../Blockchain.md)