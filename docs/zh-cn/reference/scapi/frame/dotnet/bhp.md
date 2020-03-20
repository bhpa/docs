# BHP 命名空间

BHP 命名空间是 BHP 区块链所提供的 API，提供了访问区块链账本数据的和操作持久化存储区的方法。这些 API 分为两类。

1、区块链账本。合约程序可以通过交互服务来访问到整个区块链上的所有数据，包括完整的区块和交易，以及他们的每一个字段。

2、持久化存储区。部署在 BHP 上的每一个应用合约都有一块仅可由该合约本身来存取的存储空间，可以用来存取合约中的数据。

## 类

|                                         | 类                                                  | 说明                                       |
| --------------------------------------- | --------------------------------------------------- | ------------------------------------------ |
| ![class](../../../../assets/class.jpeg) | [Account](bhp/Account.md)                           | 表示账户的类，提供了查询余额的方法         |
| ![class](../../../../assets/class.jpeg) | [Asset](bhp/Asset.md)                               | 用来表示资产的数据结构                     |
| ![class](../../../../assets/class.jpeg) | [Block](bhp/Block.md)                               | 表示区块的类，提供了查询区块中交易的方法   |
| ![class](../../../../assets/class.jpeg) | [Blockchain](bhp/Blockchain.md)                     | 该类提供了访问区块链数据的一系列方法       |
| ![class](../../../../assets/class.jpeg) | [Contract](bhp/Contract.md)                         | 表示合约的类                               |
| ![class](../../../../assets/class.jpeg) | [Header](bhp/Header.md)                             | 用来表示区块头的数据结构                   |
| ![class](../../../../assets/class.jpeg) | [Runtime](bhp/Runtime.md)                           | 提供智能合约运行时的一些方法               |
| ![class](../../../../assets/class.jpeg) | [Storage](bhp/Storage.md)                           | 提供了持久化存储区的插入、查询、删除的方法 |
| ![class](../../../../assets/class.jpeg) | [StorageContext](bhp/StorageContext.md)             | 用来表示私有存储区存储上下文的类           |
| ![class](../../../../assets/class.jpeg) | [Transaction](bhp/Transaction.md)                   | 用来表示交易的基类                         |
| ![class](../../../../assets/class.jpeg) | [TransactionAttribute](bhp/TransactionAttribute.md) | 用来表示交易特性的数据结构                 |
| ![class](../../../../assets/class.jpeg) | [TransactionInput](bhp/TransactionInput.md)         | 用来表示交易输入的数据结构                 |
| ![class](../../../../assets/class.jpeg) | [TransactionOutput](bhp/TransactionOutput.md)       | 用来表示交易输出的数据结构                 |
| ![class](../../../../assets/class.jpeg) | [Validator](bhp/Validator.md)                       | 提供共识节点的一些方法                     |

## 枚举

|                                       | 枚举                              | 说明                           |
| ------------------------------------- | --------------------------------- | ------------------------------ |
| ![enum](../../../../assets/enum.jpeg) | [TriggerType](bhp/TriggerType.md) | 用来表示智能合约触发条件的枚举 |

