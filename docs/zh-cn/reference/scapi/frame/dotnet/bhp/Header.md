# Header 类

用来表示区块头的数据结构。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public class Header : IScriptContainer
```

## 属性

|                                          | 名称                                       | 说明                         |
| ---------------------------------------- | ---------------------------------------- | -------------------------- |
| ![attribute](../../../../../assets/attribute.jpeg) | [ConsensusData](Header/ConsensusData.md) | 获得该区块的共识数据（共识节点生成的伪随机数）    |
| ![attribute](../../../../../assets/attribute.jpeg) | [Hash](Header/ConsensusData.md)          | 获得该区块的散列                   |
| ![attribute](../../../../../assets/attribute.jpeg) | [Index](Header/Index.md)                 | 获得该区块的高度                   |
| ![attribute](../../../../../assets/attribute.jpeg) | [MerkleRoot](Header/MerkleRoot.md)       | 获得该区块中所有交易的 Merkle Tree 的根 |
| ![attribute](../../../../../assets/attribute.jpeg) | [NextConsensus](Header/NextConsensus.md) | 获得下一个记账合约的散列值              |
| ![attribute](../../../../../assets/attribute.jpeg) | [PrevHash](Header/PrevHash.md)           | 获得前一个区块的散列                 |
| ![attribute](../../../../../assets/attribute.jpeg) | [Timestamp](Header/Timestamp.md)         | 获得区块的时间戳                   |
| ![attribute](../../../../../assets/attribute.jpeg) | [Version](Header/Version.md)             | 获得区块版本号                    |

## 构造方法

通过 [Blockchain.GetHeader(byte[])](Blockchain/GetHeader.md) 来构造 Header 对象。

通过 [Blockchain.GetHeader(uint)](Blockchain/GetHeader2.md) 来构造 Header 对象。