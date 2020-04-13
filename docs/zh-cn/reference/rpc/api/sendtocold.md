# sendtocold方法

将钱包内的资产转账到指定地址。

>  [!Note] 
>
>  执行此命令前需要在 BHP-CLI 节点中打开钱包。

## 参数说明

- address：要转账的地址，该地址需为标准地址。

- asset：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过CLI命令中的 `llist asset` 命令查询，也可以在区块链浏览器中查询。默认为BHP资产。

- fee_address：bhp手续费地址，可选参数。（转账资产包含BHP时，此参数无效）

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "sendtocold",
  "params": ["ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY","0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x710fb7293cc4b883d94775ff9f847bf81b60f331abe3cfe48ee8544c22583458",
        "size": 440,
        "type": "ContractTransaction",
        "version": 0,
        "attributes": [],
        "vin": [
            {
                "txid": "0xaaa08061003c718bda8d9a236969cbeb9061be9e166b94977996e1320ff54c6c",
                "vout": 1
            },
            {
                "txid": "0x17b088ea29056fb8b7030bd694a5cf84772d4d93b61d2b4e3e4f25f6d4387ed3",
                "vout": 0
            },
           ...
        ],
        "vout": [
            {
                "n": 0,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "45747516.63541171",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "tx_fee": "0.0001",
        "scripts": [
            {
                "invocation": "407ea498941f7cf041a68a16ad92292c879fa3dcfc49ac082f19f9bfea8190aa69959e33a3566db9c4cec10c78ed6eba85a247261b55b8fe842b78ebb7463cc0b3",
                "verification": "2103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
            }
        ]
    }
}
```

