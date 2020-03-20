# Block.GetTransaction 方法 (int)

通过索引获得当前区块中指定的交易。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public extern Bhp.SmartContract.Framework.Services.Bhp.Transaction GetTransaction(int index)
```

参数：交易在区块中的索引，整型。

返回值：交易，[Transaction](../Transaction.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        Block block = Blockchain.GetBlock(997027);
        Transaction tx = block.GetTransaction(0);
    }
}
```



[返回上级](../Block.md)