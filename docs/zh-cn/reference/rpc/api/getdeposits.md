# getdeposits方法

获取指定地址的交易。

## 参数说明

- address：要获取交易的地址，该地址需为标准地址。
- position：起始索引位置，默认1
- offset：偏移量，默认20

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getdeposits",
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
                "blockHeight": "894740",
                "txid": "0x710fb7293cc4b883d94775ff9f847bf81b60f331abe3cfe48ee8544c22583458",
                "type": "ContractTransaction",
                "inputaddress": [
                    "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
                ],
                "asset": "0x07d8f52825899ce08dc2d3d8f4eda62dcaef0035719fcaa267fcdef6bd70c95c",
                "n": 1,
                "value": 20000,
                "outputaddress": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",
                "time": "2019-07-03 05:44:20",
                "utctime": 1562132660,
                "confirmations": "44"
            },
           ...
        ]
    }
}
```

响应说明：

- blockHeight：区块高度
- txid：交易ID
- type：交易类型
- inputaddress：交易输入地址
- asset：资产ID
- n：交易索引
- value：转账金额
- outputaddress：转账地址
- time：交易时间
- utctime：UTC时间
- confirmations：确认数