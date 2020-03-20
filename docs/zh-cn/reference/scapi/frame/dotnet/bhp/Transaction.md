# Transaction 类

用来表示交易的基类。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public class Transaction : IScriptContainer
```

## 属性

|                                          | 名称                          | 说明           |
| ---------------------------------------- | --------------------------- | ------------ |
| ![attribute](../../../../../assets/attribute.jpeg) | [Hash](Transaction/Hash.md) | 获得当前交易的 Hash |
| ![attribute](../../../../../assets/attribute.jpeg) | [Type](Transaction/Type.md) | 获得当前交易的类型    |

## 方法

|                                          | 名称                                       | 说明                                       |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| ![function](../../../../../assets/function.jpeg) | [GetAttributes()](Transaction/GetAttributes.md) | 查询当前交易的所有属性                              |
| ![function](../../../../../assets/function.jpeg) | [GetInputs()](Transaction/GetInputs.md)  | 查询当前交易的所有交易输入（[TransactionIntput](TransactionInput.md)） |
| ![function](../../../../../assets/function.jpeg) | [GetOutputs()](Transaction/GetOutputs.md) | 查询当前交易的所有交易输出（[TransactionOutput](TransactionOutput.md)） |
| ![function](../../../../../assets/function.jpeg) | [GetReferences()](Transaction/GetReferences.md) | 查询当前交易的所有输入所引用的交易输出                      |

## 构造方法

通过 [Blockchain.GetTransaction(byte[])](Blockchain/GetTransaction.md) 来构造 Transaction 对象。