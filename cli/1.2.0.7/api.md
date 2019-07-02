# API 参考

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
      "AutoLock": false
    },
    "PluginURL": "",
    "DataRPC": {
      "Host": "http://exp.bhpa.io:7070"
    }
  }
}
```

如果要调用与钱包相关的 API，也需要先修改配置文件 config.json，将 unlockwallet 改为 true 的状态，并填写对象钱包的文件名和密码，通过"AutoLock":true可以设置是否对钱包自动加锁，如下所示：

```
"UnlockWallet": {
      "Path": "your wallet.json",
      "Password": "your password",
      "StartConsensus": false,
      "IsActive": true,
      "AutoLock": false
    },
```

完成配置后打开 BHP-CLI，客户端会在同步到最新区块后自动打开已配置的钱包并进行钱包索引同步。

## 监听端口

JSON-RPC 服务器启动后，会监听 TCP 端口，默认端口如下。

|               | 主网（Main Net） | 测试网（Test Net） |
| ------------- | ---------------- | ------------------ |
| JSON-RPC HTTP | 20557            | 20557              |

## 命令列表

| 方法                                                         | 参数      | 说明               | 备注         |
| ------------------------------------------------------------ | --------- | ------------------ | ------------ |
| [dumpprivkey](https://github.com/BhpAlpha/docs/blob/master/cli/1.2.0.7/api/dumpprivkey.md) | <address> | 导出指定地址的私钥 | 需要打开钱包 |
|                                                              |           |                    |              |

## POST 请求示例

一次典型的 JSON-RPC Post 请求的格式如下：

下面以获取主链中区块的数量方法为例。

请求 URL：

http://exp.bhpa.io:20557
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

![api_post](https://github.com/BhpAlpha/docs/raw/master/asset/api_post.png)