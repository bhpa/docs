# 在本地主机搭建私有链

这篇文章我们将介绍如何在一台 Windows 系统的电脑上搭建私有链。

## 安装节点

首先安装 BHP-CLI，并将节点文件复制为 4 份，文件夹名分别命名为 bhp-cli1、bhp-cli2、bhp-cli3、bhp-cli4。

## 安装插件

要使节点达成共识，需要安装 SimplePolicy 插件启用共识策略。

1. 下载 [SimplePolicy](https://github.com/BhpAlpha/bhp-plugins/releases) 插件并解压。
2. 将文件夹 Plugins 拷贝四份，分别放置到四个节点文件夹中。

## 创建钱包文件

使用 BHP-CLI 或 BHP-GUI 创建四个不同的钱包文件，命名为 1.json、2.json、3.json、4.json，分别放置于四个节点的文件夹中。

## 修改 config.json

在每个节点下的 config.json 文件中进行如下修改：

- 设置每个端口不重复且不被其它程序占用。
- 设置 UnlockWallet 下的参数 `Path` 为钱包文件名，`Password` 为钱包密码。
- 设置 `StartConsensus` 和 `IsActive` 为 `true`。


可参照下面的配置：

**bhp-cli1/config.json**

```json
{
  "ApplicationConfiguration": {
    "Paths": {
      "Chain": "Chain_{0}",
      "Index": "Index_{0}"
    },
    "P2P": {
      "Port": 10555,
      "WsPort": 10556
    },
    "RPC": {
      "BindAddress": "127.0.0.1",
      "Port": 10557,
      "SslCert": "",
      "SslCertPassword": ""
    },
    "UnlockWallet": {
      "Path": "1.json",
      "Password": "***",
      "StartConsensus": true,
      "IsActive": true,
      "AutoLock": false,
      "IsBhpFee": false
    }
  }
}
```

**bhp-cli2/config.json**

```json
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
      "Path": "2.json",
      "Password": "***",
      "StartConsensus": true,
      "IsActive": true,
      "AutoLock": false,
      "IsBhpFee": false
    }
  }
}
```

**bhp-cli3/config.json**

```json
{
  "ApplicationConfiguration": {
    "Paths": {
      "Chain": "Chain_{0}",
      "Index": "Index_{0}"
    },
    "P2P": {
      "Port": 30555,
      "WsPort": 30556
    },
    "RPC": {
      "BindAddress": "127.0.0.1",
      "Port": 30557,
      "SslCert": "",
      "SslCertPassword": ""
    },
    "UnlockWallet": {
      "Path": "3.json",
      "Password": "***",
      "StartConsensus": true,
      "IsActive": true,
      "AutoLock": false,
      "IsBhpFee": false
    }
  }
}
```

**bhp-cli4/config.json**

```json
{
  "ApplicationConfiguration": {
    "Paths": {
      "Chain": "Chain_{0}",
      "Index": "Index_{0}"
    },
    "P2P": {
      "Port": 40555,
      "WsPort": 40556
    },
    "RPC": {
      "BindAddress": "127.0.0.1",
      "Port": 40557,
      "SslCert": "",
      "SslCertPassword": ""
    },
    "UnlockWallet": {
      "Path": "4.json",
      "Password": "***",
      "StartConsensus": true,
      "IsActive": true,
      "AutoLock": false,
      "IsBhpFee": false
    }
  }
}
```

## 修改 protocol.json

在每个节点下的 protocol.json 文件中，对以下参数进行修改，并保证所有节点的配置一致。

- Magic ：私有链 ID，可设置为 [0 - 4294967295] 区间内的任意整数。

- StandbyValidators ：备用共识节点的公钥，这里输入 4 个钱包的公钥。

- SeedList ：种子节点的 IP 地址和端口号，IP 地址设置为 localhost，端口为 config.json 中配置的 4 个 P2P Port。


可参照下面的配置：

```json
{
  "ProtocolConfiguration": {
    "Magic": 123456,
    "AddressVersion": 23,
    "SecondsPerBlock": 15,
    "StandbyValidators": [
      "03705ff82d610058bb8186796d3f9210c68d0cac81ab167cd69946c447f5ef4764",
      "0270d82c6d3467f5df61aec26b4d75c9fe0f4d844b3eb1ddb19fc9da81d05840a7",
      "02a26bb5f72769a55cd58ed99d0276e7d63c03e77abd31854ceef5b616e88ba781",
      "031dd7e5d70159f7f00505c3a76513f70698fb8e7134c2cb7832295966a1903c25"
    ],
    "SeedList": [
      "localhost:10555",
      "localhost:20555",
      "localhost:30555",
      "localhost:40555"
    ],
    "SystemFee": {
      "EnrollmentTransaction": 1000,
      "IssueTransaction": 500,
      "PublishTransaction": 500,
      "RegisterTransaction": 10000
    }
  }
}
```

## 启动私有链

进入每个节点目录，启动 BHP-CLI， 私链成功建立：

![private_chain](https://github.com/BhpAlpha/docs/raw/master/asset/private_chain.png)

如果关闭所有窗口，将停止私有链。

