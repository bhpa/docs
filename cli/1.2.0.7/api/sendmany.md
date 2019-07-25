# sendmany方法

批量转账命令，并且可以指定找零地址

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

<outputs_array> [fee=0] [change_address]

- outputs_array：数组，数组中的每个元素的数据结构如下：
  {"asset": \<asset>,"value": \<value>,"address": \<address>}
  - asset：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过CLI命令中的 llist asset 命令查询，也可以在区块链浏览器中查询
  - value：转账金额
  - address：收款地址

- fee：手续费，可选参数，默认为 0
- change_address：找零地址，可选参数，默认为钱包中第一个标准地址

## 调用示例

请求正文：

```
{
    "jsonrpc": "2.0",
    "method": "sendmany",
    "params": [
        [
            {
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": 1,
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            },
            {
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": 1,
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            }
        ]
    ],
    "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x55ba819b50f5821298328f3bf9bb17e088afc900cf2ad7dbfc03d49940b5cf30",
        "size": 322,
        "type": "ContractTransaction",
        "version": 0,
        "attributes": [],
        "vin": [
            {
                "txid": "0x06de043b9b914f04633c580ab02d89ba55556f775118a292adb6803208857c91",
                "vout": 1
            }
        ],
        "vout": [
            {
                "n": 0,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "1",
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            },
            {
                "n": 1,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "1",
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            },
            {
                "n": 2,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "495",
                "address": "AK5q8peiC4QKwuZHWX5Dkqhmar1TAGvZBS"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "scripts": [
            {
               "invocation": "406e545e30a6b39f71a7a40f1d4937939b9e1ca38851449842a2e2318bd499afd9c89f0c96658923e3e435ee91192e9dbf101d81a240fa7c953ac0c322d2f2b980",
                "verification": "2103cf5ba6a9135f8eaeda771658564a855c1328af6b6808635496a4f51e3d29ac3eac"
            }
        ]
    }
}
```

响应说明：

- 返回如上的交易详情说明交易发送成功，否则交易发送失败
- JSON 格式不正确，会返回 Parse error
- 如果签名不完整会返回待签名的交易
- 如果余额不足会返回错误信息