# sendtoaddressorder方法

发送一个包含订单信息的交易

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- order：订单信息。
- asset_id：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。
- address：收款地址
- value：转账金额。
- fee：手续费，可选参数，默认为 0。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "sendtoaddressorder",
  "params": ["12346","0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",1.2],
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
                "data": "053132333436"
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
        ]
    }
}
```

响应说明：

- 返回如上的交易详情说明交易发送成功，否则交易发送失败
- 如果签名不完整会返回待签名的交易
- 如果余额不足会返回错误信息