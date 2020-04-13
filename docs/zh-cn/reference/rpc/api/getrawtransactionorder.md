# getrawtransactionorder方法

查询订单交易信息。

## 参数说明

- txid：交易 ID
- verbose：可选参数，verbose 默认值为 0，verbose 为 0 时返回的是交易的序列化后的信息，用 16 进制字符串表示，如果从中获取详细信息需要调用 SDK 来进行反序列化。verbose 为 1 时返回的是对应交易的详细信息，用 Json 格式字符串表示

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getrawtransactionorder",
  "params": ["0x41d38244c83994d158964b85af5ec862b1bfad62ce59225a4793e7f1c54dee29", 1],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x41d38244c83994d158964b85af5ec862b1bfad62ce59225a4793e7f1c54dee29",
        "size": 270,
        "type": "ContractTransaction",
        "version": 0,
        "attributes": [
            {
                "usage": "Description",
                "data": "12346"
            }
        ],
        "vin": [
            {
                "txid": "0xfe863f866617cd632ca19be0a4684931a42fd13e418a2743ff9efe6ff4527010",
                "vout": 0
            }
        ],
        "vout": [
            {
                "n": 0,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "1.2",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            },
            {
                "n": 1,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "3.7999",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "tx_fee": "0.0001",
        "scripts": [
            {
                "invocation": "402036ea879997a6856dc43bf9d81ed39e3d632d94b34bba3cbf8fb25031de31791b6b18ce85f1283ae92abaf078a3e1305d503a13a948f68f73873458c65bbb3a",
                "verification": "2103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
            }
        ],
        "blockhash": "0x9cc7b6788a6336634c0e92f84abf477b5048f15891bcdb343580851c7ae46e84",
        "confirmations": 11,
        "blocktime": 1562123726
    }
}
```
