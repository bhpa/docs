# Block 类

表示区块的类，提供了查询区块中交易的方法。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public class Block : Header
```

## 方法

|                                                  | 名称                                                  | 说明                     |
| ------------------------------------------------ | ----------------------------------------------------- | ------------------------ |
| ![function](../../../../../assets/function.jpeg) | [GetTransaction(int)](Block/GetTransaction.md)        | 获得当前区块中指定的交易 |
| ![function](../../../../../assets/function.jpeg) | [GetTransactionCount()](Block/GetTransactionCount.md) | 获得当前区块中交易的数量 |
| ![function](../../../../../assets/function.jpeg) | [GetTransactions()](Block/GetTransactions.md)         | 获得当前区块中所有的交易 |

## 构造方法

通过 [Blockchain.GetBlock(byte[])](Blockchain/GetBlock.md) 来构造 Block 对象。

通过 [Blockchain.GetBlock(uint)](Blockchain/GetBlock2.md) 来构造 Block 对象。