# get_tx_list方法

获取指定地址的交易列表。

## 参数说明

- address：要获取交易的地址，该地址需为标准地址。
- position：起始索引位置，默认1
- offset：偏移量，默认20

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "get_tx_list",
  "params": ["ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY","",""],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "transaction": [
            {
                "txid": "0x710fb7293cc4b883d94775ff9f847bf81b60f331abe3cfe48ee8544c22583458",
                "blockHeight": "952678",
                "time": "2019-07-01 12:40:19",
                "type": "ContractTransaction",
                "inputaddress": [
                    "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
                ],
                "outputaddress": [
                    {
                        "n": "0",
                        "asset": "0x07d8f52825899ce08dc2d3d8f4eda62dcaef0035719fcaa267fcdef6bd70c95c",
                        "value": 100,
                        "address": "	ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY ",
                        "svalue": "100.00000000"
                    }
                ]
            },
           ...
        ]
    }
}
```

响应说明：

- txid：交易ID
- blockHeight：区块高度
- time：交易时间
- type：交易类型
- inputaddress：交易输入地址
- outputaddress：
  - n：交易索引
  - asset：资产ID
  - value：转账金额
  - address：转账地址
  - svalue：转账金额