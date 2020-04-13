# getblock方法

根据指定的散列值，返回对应的区块信息。

## 参数说明

- hash：区块散列值（根据散列值获取时）。
- verbose：可选参数，verbose 默认值为 0，verbose 为 0 时返回的是区块的序列化后的信息，用 16 进制字符串表示，如果从中获取详细信息需要调用 SDK 来进行反序列化。verbose 为 1 时返回的是对应区块的详细信息，用 Json 格式字符串表示。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getblock",
  "params": ["0x9ce9d5f0e04b360456e120ddb7263e036eb39fd2b0465da5d680e38f12b80028", 1],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "hash": "0x9ce9d5f0e04b360456e120ddb7263e036eb39fd2b0465da5d680e38f12b80028",
        "size": 578,
        "version": 0,
        "previousblockhash": "0x2ce2a11965ebe58afe3eb2aef7d3ddcd33b6151221e49b5c31f7b80cf44cf816",
        "merkleroot": "0xa6fbce28cc923c1ea360fad175044e5fd9489accd02227a504ba88a78bb05a2f",
        "time": 1562054450,
        "index": 948301,
        "nonce": "41b0265517d601bb",
        "nextconsensus": "AZUCM5Gr4VjFfmadzpmH2EbGx757VBiG2B",
        "script": {
            "invocation": "403e3abe52820c3fb2169d391e416d589ae3171972c2c9a0991ae593ccf597a3848568c898e173ce6fb2d47b875b6a179384434d9c071c15911d2050b7472018a340871a7dc62fd1792c39a11123826c4967e908e0d8eb61a5ff0844eb7e234d9deab3a5e8319a1d2dc7ca83ff6121e0cac9fc9ba9ac50bca4bca6e39a7f183bb9354002437533de3d25ce68a25bff7cb63668b094cf8cb967cfb49ba4320b5aa22a255479db9402b858f00f45f3602ac0ce7bfb2bd2f889bfe6675916f10eee70a279",
            "verification": "5321030492b9b949da9ad32fec45b596f5db0cf172a4676fae3726d35ba02e10b9f09821037801dc2903baa4163b44302f33f43e0e12999782144c871060e23a478eeaa48421029144afe6f10a4841e0787cbcca8fa297464ec9f6b9d8a1f1170e49ead5e1bc592102c61ec47f8af4b333ed5e680f194d56be78786cd22fe0638750d0dc3bec7e349654ae"
        },
        "tx": [
            {
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
                "nonce": 399901115
            }
        ],
        "confirmations": 69,
        "nextblockhash": "0x38023927e46c127952e9f306a090a9e948e32a71f115a3a84116a4fa8e212412"
    }
}
```
