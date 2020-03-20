# TransactionAttribute 类

用来表示交易特性的数据结构。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public class TransactionAttribute : IApiInterface
```

## 属性

|                                          | 名称                                     | 说明                |
| ---------------------------------------- | -------------------------------------- | ----------------- |
| ![attribute](../../../../../assets/attribute.jpeg) | [Data](TransactionAttribute/Data.md)   | 获得该交易特性中用途之外的额外数据 |
| ![attribute](../../../../../assets/attribute.jpeg) | [Usage](TransactionAttribute/Usage.md) | 获得该交易特性中的用途       |

## 构造方法

通过 Transaction 对象的 [GetAttributes()](Transaction/GetAttributes.md) 方法来构造 TransactionAttribute 对象。