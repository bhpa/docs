# getbestblockhash方法

获取主链中高度最大的区块的散列。

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getbestblockhash",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x9ce9d5f0e04b360456e120ddb7263e036eb39fd2b0465da5d680e38f12b80028"
}
```

响应说明：

- result为主链中高度最大的区块的散列