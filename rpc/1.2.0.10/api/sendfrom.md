# sendfrom方法

从指定地址，向指定地址转账

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- asset_id：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。
- from：转账地址（sendfrom使用）
- to: 收款地址（sendfrom使用）
- value：转账金额
- fee：gas手续费，可选参数，默认为 0
- change_address：找零地址，可选参数，默认为钱包中第一个标准地址
- remark：备注，可选参数
- fee_address：bhp手续费地址，可选参数

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "sendfrom",
  "params": ["0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",1,0,"ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY","hello","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0xe352354beba8cb09fdcda122d98dd87ad7bc5435d9776ccfc194bb13ab012048",
        "size": 270,
        "type": "ContractTransaction",
        "version": 0,
        "attributes": [
            {
                "usage": "Description",
                "data": "0568656c6c6f"
            }
        ],
        "vin": [
            {
                "txid": "0x2472dd3d31384e9a30baa2c265fd665bcb69c7b5567be8321a6a671266b07cf1",
                "vout": 1
            }
        ],
        "vout": [
            {
                "n": 0,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "1",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            },
            {
                "n": 1,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "3.9997",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "tx_fee": "0.0001",
        "scripts": [
            {
                "invocation": "405af283979eacbf9ae071e39d7cfca9178e2bbc399b67a010894af0fac31e35c9d55736ba48840cc2133f4ec008b05538a08c9db715ab6d68f1d329ce4ed33606",
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