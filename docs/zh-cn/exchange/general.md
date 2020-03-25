# 交易所对接指南介绍 

BHP 算力公链中的全局资产是 BHP，使用 UTXO 模型来管理资产。交易所主要处理 BHP 的充币、提币等操作。需要在本地部署 BHP 算力公链节点：bhp-cli。在 BHP 算力公链的网络中充当一个普通节点，处理 BHP 算力公链上各种资产的相关交易。

本文主要用于指导交易所完成与 BHP 对接的安装部署，程序开发和相关交易处理。

一般来说，交易所对接需要完成以下操作：

- [在服务器中部署 BHP 节点](deploynode.md)
- [使用 bhp-cli 客户端](client.md)
- [处理资产交易](transaction.md)
- [给用户分发 GAS](gas.md)

后文将进行详细描述。

> ★BHP全局资产：0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854
>
> ★BHPGAS：0xa60b5dbb2b50022e3179a5a129b4d90bbb5bf5caabc40893fcdb83703e751225
>
> ★BHP区块链浏览器：https://exp.bhpa.io
>
> ★BHP源码：https://github.com/BhpAlpha/bhp-cli
>
> 每个版本的 bhp-cli 在具体对接方法上存在差异，交易所升级客户端时请务必注意版本间差异。