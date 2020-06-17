# claimgas方法

提取钱包中的 GAS。

>  [!Note] 
>
>  执行此命令前需要在 BHP-CLI 节点中打开钱包。

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "claimgas",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txs": [
            {
                "txid": "0xe0e53513c9109cb4c36f470abfbccd178286562b6f1cfeb1120d2cb301ea3d08",
                "size": 1869,
                "type": "ClaimTransaction",
                "version": 0,
                "attributes": [],
                "vin": [],
                "vout": [
                    {
                        "n": 0,
                        "asset": "0xa60b5dbb2b50022e3179a5a129b4d90bbb5bf5caabc40893fcdb83703e751225",
                        "value": "280622.2566828",
                        "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
                    }
                ],
                "sys_fee": "0",
                "net_fee": "0",
                "tx_fee": "0",
                "scripts": [
                    {
                        "invocation": "4005defdbc98902b9bed226b5b7b4a9f6f3257511aab8b9a69a9c49f3c15a661a50a5e887655f6b05fc942a8dcacfee8995a2030a1a4212c55887eb57e80083b57",
                        "verification": "2103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
                    }
                ],
                "claims": [
                    {
                        "txid": "0x6e1abef610874bb7435751b6c4abee826a2ebe380a6d7976c82c7faa519b6c2d",
                        "vout": 0
                    },
                    {
                        "txid": "0x81dba5a6043e6bcc6bc7bfc2874a540718055490e003bbed0ee41f4a7fe8cb86",
                        "vout": 0
                    },
                    ......
                ]
            },
            ......
        ]
    }
}
```

响应说明：

返回所有交易的内容。