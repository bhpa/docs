# gettransactionheight方法

获取交易高度

## 参数说明

txid：交易id。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "gettransactionheight",
  "params": ["0xa6fbce28cc923c1ea360fad175044e5fd9489accd02227a504ba88a78bb05a2f", 1],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 948301
}
```

响应说明：

- 返回该交易的高度。