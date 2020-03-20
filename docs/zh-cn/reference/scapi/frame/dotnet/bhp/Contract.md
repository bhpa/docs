# Contract 类

表示合约的类。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public class Contract
```

## 属性

|                                                    | 名称                         | 说明                 |
| -------------------------------------------------- | ---------------------------- | -------------------- |
| ![attribute](../../../../../assets/attribute.jpeg) | [Script](Contract/Script.md) | 获得该合约的脚本散列 |

## 方法

|                                          | 名称                                       | 说明              |
| ---------------------------------------- | ---------------------------------------- | --------------- |
| ![function](../../../../../assets/function.jpeg) | [Create(byte[], byte[], byte, bool, string, string, string, string, string)](Contract/Create.md) | 发布智能合约    |
| ![function](../../../../../assets/function.jpeg) | [Migrate(byte[], byte[], byte, bool, string, string, string, string, string)](Contract/Migrate.md) | 迁移 / 更新智能合约 |
| ![function](../../../../../assets/function.jpeg) | [Destroy()](Contract/Destroy.md)         | 销毁智能合约    |

## 构造方法

通过 [Blockchain.GetContract(byte[])](Blockchain/GetContract.md) 方法来构造 Contract 对象。

通过 [Contract.Create(byte[], byte[], byte, bool, string, string, string, string, string)](Contract/Create.md) 方法来发布智能合约到区块链上，并返回 Contract 对象。

通过 [Contract.Migrate(byte[], byte[], byte, bool, string, string, string, string, string)](Contract/Migrate.md) 方法来更新智能合约，并返回 Contract 对象。

