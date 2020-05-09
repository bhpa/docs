# getclaimable 方法

返回指定地址内可以 claim 的 GAS 信息。

> 此方法由插件提供，需要安装 [RpcSystemAssetTracker](https://github.com/BhpAlpha/bhp-plugins/releases) 插件才可以调用。

## 参数说明

address ：指定要查询的账户地址。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getclaimable",
  "params": ["0x51afd1c72987b773049414c1f96c6b83d4977c6f"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "claimable": [],
        "address": "ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy",
        "unclaimed": 0
    }
}
```
