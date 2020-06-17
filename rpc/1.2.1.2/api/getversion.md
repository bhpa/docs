# getversion方法

获取查询节点的版本信息。

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getversion",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "port": 10555,
        "nonce": 1157787460,
        "useragent": "/Bhp:1.2.1.0/"
    }
}
```

