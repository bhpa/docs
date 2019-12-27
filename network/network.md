# 主网与测试网

BHP 的节点默认运行在主网，主网是正式上线，独立运行的区块链网络。

BHP 的测试网（Test Net）是官方提供的，专供用户来开发、调试和测试的。测试网上面的系统费用是测试网中的 BbpGas，并非真实的 BbpGas。

测试网的所有区块数据都是独立于主网的。如果开发简单的智能合约或者尝试注册资产的话，用测试网就足够了，待开发完成后可以迁移到 BHP 的主网上运行。

## 测试网的特点

- 资产注册、资产分发、合约执行等不会消耗真实货币。
- 全球化的，部署在 Internet 环境上的。
- 测试网中的区块、交易等信息可以在区块链浏览器中方便地查看到。
- 部署在测试环境上的智能合约，全世界任何人都可以调用。
- 测试网不能作为商业应用的实际落地环境。

## 切换到测试网

下载BHP客户端后，可以通过修改客户端的配置文件来让客户端在主网和测试网中切换。以下步骤以 BHP-GUI为例，BHP-CLI操作相同。

1. 将客户端目录下的 `protocol.testnet.json` 里的内容复制到 `protocol.json`（替换原有配置文件），如图。


![protocol](https://github.com/BhpAlpha/docs/raw/master/asset/protocol.png)

2. 将客户端（GUI）目录下的 `config.testnet.json` 里的内容复制到 `config.json`（替换原有配置文件），如图


![config](https://github.com/BhpAlpha/docs/raw/master/asset/config.png)

## 其它测试方法

在发布智能合约到主网前，使用测试网进行试验无疑是个好办法，但是在开发初期，您还可以考虑其他测试方式，例如运行您自己的私人测试网。





