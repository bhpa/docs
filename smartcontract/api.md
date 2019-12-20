# Bhp 命名空间

Bhp 命名空间是 Bhp 区块链所提供的 API，提供了访问区块链账本数据的和操作持久化存储区的方法。

从区块链查询数据的 API：

| API                           | 说明                                |
| ----------------------------- | ----------------------------------- |
| Bhp.Blockchain.GetHeight      | 获得当前区块高度                    |
| Bhp.Blockchain.GetHeader      | 通过区块高度或区块 Hash，查找区块头 |
| Bhp.Blockchain.GetBlock       | 通过区块高度或区块 Hash，查找区块   |
| Bhp.Blockchain.GetTransaction | 通过交易 ID 查找交易                |
| Bhp.Blockchain.GetAccount     | 根据合约脚本的散列来获得一个账户    |
| Bhp.Blockchain.GetValidators  | 获得共识人的公钥                    |
| Bhp.Blockchain.GetAsset       | 根据资产 ID 查找资产                |
| Bhp.Blockchain.GetContract    | 根据合约散列获取合约内容            |

区块类 API：

| API                           | 说明                                           |
| ----------------------------- | ---------------------------------------------- |
| Bhp.Header.GetHash            | 获得该区块的散列                               |
| Bhp.Header.GetVersion         | 获得区块版本号                                 |
| Bhp.Header.GetPrevHash        | 获得前一个区块的散列                           |
| Bhp.Header.GetIndex           | 获得该区块的高度                               |
| Bhp.Header.GetMerkleRoot      | 获得该区块中所有交易的 Merkle Tree 的根        |
| Bhp.Header.GetTimestamp       | 获得区块的时间戳                               |
| Bhp.Header.GetConsensusData   | 获得该区块的共识数据（共识节点生成的伪随机数） |
| Bhp.Header.GetNextConsensus   | 获得下一个记账合约的散列值                     |
| Bhp.Block.GetTransactionCount | 获得当前区块中交易的数量                       |
| Bhp.Block.GetTransactions     | 获得当前区块中所有的交易                       |
| Bhp.Block.GetTransaction      | 获得当前区块中指定的交易                       |

交易类 API：

| API                           | 说明                                         |
| ----------------------------- | -------------------------------------------- |
| Bhp.Transaction.GetHash       | 获得当前交易的 Hash                          |
| Bhp.Transaction.GetType       | 获得当前交易的类型                           |
| Bhp.Transaction.GetAttributes | 查询当前交易的所有属性                       |
| Bhp.Transaction.GetInputs     | 查询当前交易的所有交易输入                   |
| Bhp.Transaction.GetOutputs    | 查询当前交易的所有交易输出                   |
| Bhp.Transaction.GetReferences | 查询当前交易的所有输入所引用的交易输出       |
| Bhp.Attribute.GetUsage        | 获得该交易特性中的用途                       |
| Bhp.Attribute.GetData         | 获得该交易特性中用途之外的额外数据           |
| Bhp.Input.GetHash             | 所引用的交易的交易散列                       |
| Bhp.Input.GetIndex            | 所引用的交易输出在其全部交易输出列表中的索引 |
| Bhp.Output.GetAssetId         | 获得资产 ID                                  |
| Bhp.Output.GetValue           | 获得交易金额                                 |
| Bhp.Output.GetScriptHash      | 获得脚本散列                                 |

账户类 API：

| API                       | 说明                                   |
| ------------------------- | -------------------------------------- |
| Bhp.Account.GetScriptHash | 获得该合约账户的脚本散列               |
| Bhp.Account.GetVotes      | 获得该合约账户投给其它人的的投票信息   |
| Bhp.Account.GetBalance    | 通过资产 ID 获得该账户中这种资产的余额 |

资产类 API：

| API                    | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Bhp.Asset.GetAssetId   | 获得该资产的 ID                                              |
| Bhp.Asset.GetAssetType | 获得该资产的类别                                             |
| Bhp.Asset.GetAmount    | 获得该资产的总量                                             |
| Bhp.Asset.GetAvailable | 获得该资产的已经发行出去的数量                               |
| Bhp.Asset.GetPrecision | 获得该资产的精度（最小分割数量），单位为小数点之后的位数     |
| Bhp.Asset.GetOwner     | 获得该资产的所有人（公钥）                                   |
| Bhp.Asset.GetAdmin     | 获得该资产的管理员（合约地址），有权对资产的属性（如总量，名称等）进行修改 |
| Bhp.Asset.GetIssuer    | 获得该资产的发行人（合约地址），有权进行资产的发行           |

合约类 API：

| API                    | 说明             |
| ---------------------- | ---------------- |
| Bhp.Contract.GetScript | 获得该合约的脚本 |

存储类 API：

| API                    | 说明                                                |
| ---------------------- | --------------------------------------------------- |
| Bhp.Storage.GetContext | 获取当前存储区上下文                                |
| Bhp.Storage.Get        | 查询操作，在持久化存储区中通过 key 查询对应的 value |

运行时相关的 API：

| API                      | 说明                                                    |
| ------------------------ | ------------------------------------------------------- |
| Bhp.Runtime.GetTrigger   | 获得该智能合约的触发条件（应用合约 or 鉴权合约）        |
| Bhp.Runtime.CheckWitness | 验证调用该智能合约的交易 / 区块是否验证过所需的脚本散列 |
| Bhp.Runtime.Notify       | 在智能合约中向执行该智能合约的客户端发送通知            |
| Bhp.Runtime.Log          | 在智能合约中向执行该智能合约的客户端发送日志            |

------

此类 API 会对智能合约的状态进行修改

| API                            | 说明                                                  |
| ------------------------------ | ----------------------------------------------------- |
| Bhp.Account.SetVotes           | 设置该合约账户投给其它人的的投票信息                  |
| Bhp.Validator.Register         | 报名成为共识人                                        |
| Bhp.Asset.Create               | 注册一种资产                                          |
| Bhp.Asset.Renew                | 为资产续费                                            |
| Bhp.Contract.Create            | 发布智能合约                                          |
| Bhp.Contract.Migrate           | 迁移 / 更新智能合约                                   |
| Bhp.Contract.Destroy           | 销毁合约                                              |
| Bhp.Contract.GetStorageContext | 获得合约的存储上下文                                  |
| Bhp.Storage.Put                | 插入操作，以 key-value 的形式向持久化存储区中插入数据 |
| Bhp.Storage.Delete             | 删除操作，在持久化存储区中通过 key 删除对应的 value   |

# System 命名空间

System 命名空间是智能合约执行引擎（BhpVM）提供的 API，提供了访问该智能合约的执行环境的方法。

| API                                           | 说明                                                 |
| --------------------------------------------- | ---------------------------------------------------- |
| System.ExecutionEngine.GetScriptContainer     | 获得该智能合约的脚本容器（最开始的触发者）           |
| System.ExecutionEngine.GetExecutingScriptHash | 获得该智能合约执行的脚本散列                         |
| System.ExecutionEngine.GetCallingScriptHash   | 获得该智能合约的调用者的脚本散列                     |
| System.ExecutionEngine.GetEntryScriptHash     | 获得该智能合约的入口点（合约调用链的起点）的脚本散列 |

