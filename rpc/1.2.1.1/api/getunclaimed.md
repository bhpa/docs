# getunclaimed 方法

返回指定地址中未提取的 GAS 数量。

> 此方法由插件提供，需要安装 [RpcSystemAssetTracker](https://github.com/BhpAlpha/bhp-plugins/releases) 插件才可以调用。

## 参数说明

address ：指定要查询的账户地址。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getunclaimed",
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
        "available": 0,
        "unavailable": 41649.29907446,
        "unclaimed": 41649.29907446
    }
}
```
