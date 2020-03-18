# API 参考

> 修改：
>
> - sendfrom
> - sendmany
> - sendtoaddress
> - sendtoaddressorder
> - sendtocold
> - gettransactiondata

每个 BHP 节点 Bhp-CLI 都可选的提供了一套 API 接口，用于从节点获取区块链数据，使得开发区块链应用变得十分方便。接口通过 JSON-RPC 的方式提供，底层使用 HTTP/HTTPS 协议进行通讯。要启动一个提供 RPC 服务的节点，可运行以下命令：

```
dotnet bhp-cli.dll --rpc
```

## 修改配置文件

若要通过 HTTPS 的方式访问 RPC 服务器，需要在启动节点前修改配置文件 config.json。

```
{
  "ApplicationConfiguration": {
    "Paths": {
      "Chain": "Chain_{0}",
      "Index": "Index_{0}"
    },
    "P2P": {
      "Port": 20555,
      "WsPort": 20556
    },
    "RPC": {
      "BindAddress": "127.0.0.1",
      "Port": 20557,
      "SslCert": "",
      "SslCertPassword": ""
    },
    "UnlockWallet": {
      "Path": "",
      "Password": "",
      "StartConsensus": false,
      "IsActive": false,
      "AutoLock": false,
      "IsBhpFee":false
    },
    "PluginURL": "",
    "DataRPC": {
      "Host": "http://exp.bhpa.io:7070"
    },
    "ExportWallet": {
      "Path": "",
      "Interval": 8,
      "IsActive": false
    }
  }
}
```

如果要调用与钱包相关的 API，也需要先修改配置文件 config.json，将 unlockwallet 改为 true 的状态，并填写对象钱包的文件名和密码，通过"AutoLock":true可以设置是否对钱包自动加锁。将IsBhpFee设置为true，代币转账将会收取手续费。如下所示：

```
"UnlockWallet": {
      "Path": "your wallet.json",
      "Password": "your password",
      "StartConsensus": false,
      "IsActive": true,
      "AutoLock": false,
      "IsBhpFee":false
    },
```

配置ExportWallet将会导出钱包地址的私密信息（WIF，私钥，公钥，地址），请谨慎使用。Path为导出路径，Interval为导出间隔，单位小时，IsActive设置为true，则定时导出。如下所示：

```
  "ExportWallet": {
      "Path": "D:\\wallets",
      "Interval": 8,
      "IsActive": false
    }
```

完成配置后打开 BHP-CLI，客户端会在同步到最新区块后自动打开已配置的钱包并进行钱包索引同步。

## 监听端口

JSON-RPC 服务器启动后，会监听 TCP 端口，默认端口如下。

|               | 主网（Main Net） | 测试网（Test Net） |
| ------------- | ---------------- | ------------------ |
| JSON-RPC HTTP | 20557            | 20557              |

## 命令列表

| 方法                                                         | 参数                                                         | 说明                                                 | 备注                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------------------------------------- | --------------------------- |
| [getnewaddress](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getnewaddress.md) |                                                              | 创建一个新的地址                                     | 需要打开钱包                |
| [listaddress](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/listaddress.md) |                                                              | 列出当前钱包内的所有地址                             | 需要打开钱包                |
| [dumpprivkey](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/dumpprivkey.md) | < address >                                                  | 导出指定地址的私钥                                   | 需要打开钱包                |
| [exportaddresswif](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/exportaddresswif.md) | < address >                                                  | 获取地址的相关信息                                   | 需要打开钱包                |
| [validateaddress](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/validateaddress.md) | < address >                                                  | 验证地址是否是正确的BHP地址                          |                             |
| [getaccountstate](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getaccountstate.md) | < address >                                                  | 根据账户地址，查询账户资产信息                       |                             |
| [getassetstate](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getassetstate.md) | < asset_id >                                                 | 根据指定的资产编号，查询资产信息                     |                             |
| [getbalance](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getbalance.md) | < asset_id >                                                 | 根据指定的资产编号，返回钱包中对应资产的余额信息     | 需要打开钱包                |
| [getblockcount](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getblockcount.md) |                                                              | 获取主链中区块的数量                                 |                             |
| [getbestblockhash](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getbestblockhash.md) |                                                              | 获取主链中高度最大的区块的散列                       |                             |
| [getblockhash](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getblockhash.md) | < index >                                                    | 根据指定的索引，返回对应区块的散列值                 |                             |
| [getblock](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getblock.md) | < hash > [verbose=0]                                         | 根据指定的散列值，返回对应的区块信息                 |                             |
| [getblock](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getblock2.md) | < index > [verbose=0]                                        | 根据指定的索引，返回对应的区块信息                   |                             |
| [getblockheader](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getblockheader.md) | < hash > [verbose=0]                                         | 根据指定的散列值，返回对应的区块头信息。             |                             |
| [getpeers](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getpeers.md) |                                                              | 获得该节点当前已连接/未连接的节点列表                |                             |
| [getconnectioncount](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getconnectioncount.md) |                                                              | 获取节点当前的连接数                                 |                             |
| [getversion](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getversion.md) |                                                              | 获取查询节点的版本信息                               |                             |
| [getvalidators](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getvalidators.md) |                                                              | 查看当前共识节点的信息                               |                             |
| [getcontractstate](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getcontractstate.md) | < script_hash >                                              | 根据合约脚本散列，查询合约信息                       |                             |
| [invoke](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/invoke.md) | < script_hash > < params >                                   | 使用给定的参数以散列值调用智能合约                   |                             |
| [invokefunction](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/invokefunction.md) | < script_hash > < operation > < params >                     | 以指定的脚本散列值调用智能合约，传入操作及参数       |                             |
| [invokescript](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/invokescript.md) | < script >                                                   | 通过虚拟机运行脚本并返回结果                         |                             |
| [sendrawtransaction](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendrawtransaction.md) | < hex >                                                      | 广播交易                                             |                             |
| [getrawmempool](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getrawmempool.md) |                                                              | 获取内存中未确认的交易列表                           |                             |
| [getrawtransaction](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getrawtransaction.md) | < txid > [verbose=0]                                         | 根据指定的散列值，返回对应的交易信息                 |                             |
| [gettransactionheight](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/gettransactionheight.md) | < txid >                                                     | 获取交易高度。                                       |                             |
| [gettxout](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/gettxout.md) | < txid > < n >                                               | 根据指定的散列和索引，返回对应的交易输出（零钱）信息 |                             |
| [getstorage](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getstorage.md) | < script_hash > < key >                                      | 根据合约脚本散列和存储的 key，返回存储的 value       |                             |
| [getblocksysfee](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getblocksysfee.md) | < index >                                                    | 根据指定的索引，返回截止到该区块前的系统手续费       |                             |
| [getwalletheight](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getwalletheight.md) |                                                              | 获取当前钱包索引高度                                 | 需要打开钱包                |
| [unlock](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/unlock.md) | < password >< seconds >                                      | 解锁钱包                                             | 需要打开钱包                |
| [getutxos](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getutxos.md) | < address >[asset_id]                                        | 获取指定地址的未花费UTXO                             | 需要打开钱包                |
| [sendfrom](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendfrom.md) | < asset_id > < from >< to > < value > [fee=0] [change_address] [remark] [fee_address] | 从指定地址，向指定地址转账                           | 需要打开钱包                |
| [sendtoaddress](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendtoaddress.md) | < asset_id > < address > < value > [fee=0] [change_address] [fee_address] | 向指定地址转账                                       | 需要打开钱包                |
| [sendmany](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendmany.md) | < outputs_array > [fee=0] [change_address] [fee_address]     | 批量转账命令                                         | 需要打开钱包                |
| [sendtocold](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendtocold.md) | < address > [asset_id] [fee_address]                         | 将钱包内的资产转账到指定地址                         | 需要打开钱包                |
| [submitblock](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/submitblock.md) | < hex >                                                      | 提交新的区块                                         | 需要成为共识节点            |
| [gettransactiondata](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/gettransactiondata.md) | < asset_id > < address > < value > [fee=0] [change_address] [fee_address] | 获取交易的十六进制字符串                             | 需要打开钱包                |
| [verifytx](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/verifytx.md) | < hex >                                                      | 验证交易是否有效                                     |                             |
| [showgas](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/showgas.md) |                                                              | 返回本钱包的bhpgas                                   | 需要打开钱包                |
| [claimgas](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/claimgas.md) |                                                              | 提取bhpgas                                           | 需要打开钱包                |
| [sendissuetransaction](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendissuetransaction.md) | < asset_id >< outputs_array >                                | 分发资产                                             | 需要打开钱包                |
| [listsinceblock](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/listsinceblock.md) | < start_height >[target_confirmations]                       | 根据参数返回与钱包相关的所有交易                     | 需要打开钱包                |
| [sendtoaddressorder](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/sendtoaddressorder.md) | < order >< asset_id > < address > < value > [fee=0] [change_address] [fee_address] | 发送一个包含订单信息的交易                           | 需要打开钱包                |
| [getrawtransactionorder](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getrawtransactionorder.md) | < txid > [verbose=0]                                         | 根据指定的散列值，返回对应的交易信息                 |                             |
| [get_tx_list](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/get_tx_list.md) | < address >< position>< offset>                              | 获取指定地址的交易列表                               |                             |
| [gettransaction](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/gettransaction.md) | < address >< position>< offset>                              | 获取指定地址的交易                                   |                             |
| [getutxoofaddress](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getutxoofaddress.md) | < address >                                                  | 获取指定地址的未花费UTXO                             |                             |
| [getapplicationlog](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.10/api/getapplicationlog.md) | < txid >                                                     | 根据指定的 BRC-6 交易 ID 获取合约日志                | 需要安装ApplicationLogs插件 |

## POST 请求示例

一次典型的 JSON-RPC Post 请求的格式如下：

下面以获取主链中区块的数量方法为例。

请求 URL：

`http://exp.bhpa.io:20557`

请求 Body：

```
{
  "jsonrpc": "2.0",
  "method": "getblockcount",
  "params": [],
  "id": 1
}
```


发送请求后，将会得到如下的响应：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 890746
}
```

**注：当使用离线同步包同步区块时，程序可能无法响应 API 请求，建议将区块同步到最新高度后再使用 API，否则返回的结果可能不是最新的。**

## 测试工具

你可以用 Chrome 扩展程序中的 Postman 来方便地进行测试（安装 Chrome 扩展程序需要科学上网），下面是测试截图：

![api_post](../assets/api_post.png)