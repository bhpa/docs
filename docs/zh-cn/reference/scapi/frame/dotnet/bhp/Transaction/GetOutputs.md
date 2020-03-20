# Transaction.GetOutputs 方法 ()

查询当前交易的所有交易输出。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public extern Bhp.SmartContract.Framework.Services.Bhp.TransactionOutput[] GetOutputs()
```

返回值：当前交易的所有交易输出，[TransactionOutput](../TransactionOutput.md) 数组。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] transaction = new byte[] { 115,96,59,84,98,14,63,134,141,6,185,214,139,61,142,84,11,133,151,93,155,238,35,4,58,1,27,183,33,185,60,238 };
        Transaction tx = Blockchain.GetTransaction(transaction);
        TransactionOutput[] outputs = tx.GetOutputs();
    }
}
```



[返回上级](../Transaction.md)