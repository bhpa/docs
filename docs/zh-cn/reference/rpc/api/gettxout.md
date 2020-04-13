# gettxout方法

根据指定的散列和索引，返回对应的 unspent 交易输出（零钱）信息。如果交易输出已经花费，返回结果为空。

## 参数说明

- txid：交易 ID
- n：要获取的交易输出在该交易中的索引（从 0 开始）

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "gettxout",
  "params": ["0xa6fbce28cc923c1ea360fad175044e5fd9489accd02227a504ba88a78bb05a2f", 0],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "n": 0,
        "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
        "value": "4.69",
        "address": "ATnrnNybQyZSBJCgm9VtnqnTgCCxFKptQS"
    }
}
```

