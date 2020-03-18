# listsinceblock方法

根据参数返回与钱包相关的所有交易。

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- start_height：开始的区块高度（包含该区块）
- target_confirmations：目标确认数，默认6

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "listsinceblock",
  "params": [950000,1],
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
                "blockheight": 952441,
                "blockhash": "0xe38e23dac04a4ab06f8da0b4d1c418bddc5519f7fe9837a59020735b72f0de5e",
                "utctime": 1562120682
            },
            {
                "txid": "0x91a173c02ab1bc687643297dd278599be218e2e3df9f4316a56946375447730b",
                "blockheight": 952441,
                "blockhash": "0xe38e23dac04a4ab06f8da0b4d1c418bddc5519f7fe9837a59020735b72f0de5e",
                "utctime": 1562120682
            },
            ......
        ],
        "lastblockheight": 952569
    }
}
```

