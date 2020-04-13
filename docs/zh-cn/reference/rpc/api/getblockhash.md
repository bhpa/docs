# getblockhash方法

根据指定的索引，返回对应区块的散列值。

## 参数说明

index：区块索引

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getblockhash",
  "params": [2082],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0xbd9324037fcaa4f6f73e71ba00aaeb2619529014944cb2f486023abf7e73a2d8"
}
```
