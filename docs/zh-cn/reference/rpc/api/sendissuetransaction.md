# sendissuetransaction方法

分发资产

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。只有该资产注册时设置的资产发行人可发行该资产。

## 参数说明

- asset_id：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。

- <outputs_array>

  outputs_array：数组，数组中的每个元素的数据结构如下：
  {"address": \<address>,"value": \<value>}

  - address：收款地址
  - value：转账金额

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "sendissuetransaction",
  "params": [
    "0x477d3fede2d2877311bd6e2ae15b1f8d85748875832b03c1de1617f4e25b8ef8",
    [
      {
        "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",
        "value": "2"
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
        "txid": "0x2653b37ab99ae57f78bcffbe636c1afa51b2818f46f79b074d8f783984ef681a",
        "size": 262,
        "type": "IssueTransaction",
        "version": 1,
        "attributes": [],
        "vin": [
            {
                "txid": "0xe494c0d54e35ea0a29305fb06ca24aa29765be5f446f4e72a65f0f893ec4d219",
                "vout": 0
            }
        ],
        "vout": [
            {
                "n": 0,
                "asset": "0x477d3fede2d2877311bd6e2ae15b1f8d85748875832b03c1de1617f4e25b8ef8",
                "value": "2",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            },
            {
                "n": 1,
                "asset": "0xa60b5dbb2b50022e3179a5a129b4d90bbb5bf5caabc40893fcdb83703e751225",
                "value": "0.64418228",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            }
        ],
        "sys_fee": "0",
        "net_fee": "1",
        "tx_fee": "0",
        "scripts": [
            {
                "invocation": "40f18a546b2b172cb9aa28014b48d5a85e9890fd38b7ffd931b1da9f3f218ee9b2304cd6c8000bb3276bb0e53287c29428fbce4f36f05ae05a434e14126880a848",
                "verification": "2103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
            }
        ]
    }
}
```

