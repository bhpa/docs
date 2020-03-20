# Blockchain 类

该类提供了访问区块链数据的一系列方法。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static class Blockchain
```

## 方法

|                                                  | 名称                                                   | 说明                                     |
| ------------------------------------------------ | ------------------------------------------------------ | ---------------------------------------- |
| ![function](../../../../../assets/function.jpeg) | [GetAccount(byte[])](Blockchain/GetAccount.md)         | 根据合约脚本的散列来获得一个账户（地址） |
| ![function](../../../../../assets/function.jpeg) | [GetAsset(byte[])](Blockchain/GetAsset.md)             | 根据资产 ID 查找资产                     |
| ![function](../../../../../assets/function.jpeg) | [GetBlock(byte[])](Blockchain/GetBlock.md)             | 通过区块 hash ，查找区块                 |
| ![function](../../../../../assets/function.jpeg) | [GetBlock(uint)](Blockchain/GetBlock2.md)              | 通过区块高度，查找区块                   |
| ![function](../../../../../assets/function.jpeg) | [GetContract(byte[])](Blockchain/GetContract.md)       | 通过合约散列获取合约内容                 |
| ![function](../../../../../assets/function.jpeg) | [GetHeader(byte[])](Blockchain/GetHeader.md)           | 通过区块 hash ，查找区块头               |
| ![function](../../../../../assets/function.jpeg) | [GetHeader(uint)](Blockchain/GetHeader2.md)            | 通过区块高度，查找区块头                 |
| ![function](../../../../../assets/function.jpeg) | [GetHeight()](Blockchain/GetHeight.md)                 | 获得当前区块高度                         |
| ![function](../../../../../assets/function.jpeg) | [GetTransaction(byte[])](Blockchain/GetTransaction.md) | 通过交易 ID 查找交易                     |
| ![function](../../../../../assets/function.jpeg) | [GetValidators()](Blockchain/GetValidators.md)         | 获得共识人的公钥                         |

# 构造方法

BlockChain 类是静态类，无需构造方法。