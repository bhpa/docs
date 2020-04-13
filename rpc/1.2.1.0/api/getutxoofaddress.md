# getutxoofaddress方法

获取指定地址的未花费 UTXO。

## 参数说明

- address：要查询的地址，该地址需为标准地址。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getutxoofaddress",
  "params": ["ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "utxo": [
            {
                "asset": "0x07d8f52825899ce08dc2d3d8f4eda62dcaef0035719fcaa267fcdef6bd70c95c",
                "txid": "0x710fb7293cc4b883d94775ff9f847bf81b60f331abe3cfe48ee8544c22583458",
                "n": 1,
                "value": 2,
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",
                "blockHeight": 873096
            },
            ...
        ]
    }
}
```

响应说明：

- asset：资产ID
- txid：交易ID
- n：交易索引
- value：转账金额
- address：地址
- blockHeight：区块高度