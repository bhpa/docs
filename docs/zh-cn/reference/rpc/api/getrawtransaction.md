# getrawtransaction方法

根据指定的散列值，返回对应的交易信息

## 参数说明

- txid：交易 ID
- verbose：可选参数，verbose 默认值为 0，verbose 为 0 时返回的是交易的序列化后的信息，用 16 进制字符串表示，如果从中获取详细信息需要调用 SDK 来进行反序列化。verbose 为 1 时返回的是对应交易的详细信息，用 Json 格式字符串表示

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getrawtransaction",
  "params": ["0xa6fbce28cc923c1ea360fad175044e5fd9489accd02227a504ba88a78bb05a2f", 1],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0xa6fbce28cc923c1ea360fad175044e5fd9489accd02227a504ba88a78bb05a2f",
        "size": 136,
        "type": "MinerTransaction",
        "version": 0,
        "attributes": [
            {
                "usage": "MinerSignature",
                "data": "ddcd7ba40f3cf22066d39295ee60727ef662408f4603e3ba1de0695362e200081cf6456c92e729e8e299eb65113be5ed0e15838c4377a1165b228b2f8bad35bf"
            }
        ],
        "vin": [],
        "vout": [
            {
                "n": 0,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "4.69",
                "address": "ATnrnNybQyZSBJCgm9VtnqnTgCCxFKptQS"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "tx_fee": "0",
        "scripts": [],
        "nonce": 399901115,
        "blockhash": "0x9ce9d5f0e04b360456e120ddb7263e036eb39fd2b0465da5d680e38f12b80028",
        "confirmations": 232,
        "blocktime": 1562054450
    }
}
```

