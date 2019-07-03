# verifytx方法

验证交易是否有效

## 参数说明

hex：交易的十六进字符串

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "verifytx",
  "params": ["8000000299f46ee7285a4080518a83ffbbf265b865cfb02c5c14759f4deeef85676c6612010062b3d6e8123e72a5859e87e65aea90bc7a4018fcc53b090f95658f41c7067cf601000354a80a4c72f6157a7af0a753fc4ac4af6b159a17634dd57fecf319feab6ff713000e2707000000008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc54a80a4c72f6157a7af0a753fc4ac4af6b159a17634dd57fecf319feab6ff713d9dc1101000000008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc2512753e7083dbfc9308c4abcaf55bbb0bd9b429a1a579312e02502bbb5d0ba654b8a405000000008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc014140ca72f6d7984b81426632d3a0bd52a81398e1c1c7317fc667124d6c87a8782f0ae8fb3daeacf7557bcba80ee34a9b22036bd2f5294540cb2e5e84fc1edac42211232103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "result": "success",
        "tx": {
            "txid": "0x3754f3762c5f036f5c22cd7df754aa66a7ea94515fda27d729a851063cf845d1",
            "size": 356,
            "type": "ContractTransaction",
            "version": 0,
            "attributes": [],
            "vin": [
                {
                    "txid": "0x12666c6785efee4d9f75145c2cb0cf65b865f2bbff838a5180405a28e76ef499",
                    "vout": 1
                },
                {
                    "txid": "0xf67c06c7418f65950f093bc5fc18407abc90ea5ae6879e85a5723e12e8d6b362",
                    "vout": 1
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
                    "value": "0.17947865",
                    "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
                },
                {
                    "n": 2,
                    "asset": "0xa60b5dbb2b50022e3179a5a129b4d90bbb5bf5caabc40893fcdb83703e751225",
                    "value": "0.94681172",
                    "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
                }
            ],
            "sys_fee": "0",
            "net_fee": "1",
            "tx_fee": "0.0001",
            "scripts": [
                {
                    "invocation": "40ca72f6d7984b81426632d3a0bd52a81398e1c1c7317fc667124d6c87a8782f0ae8fb3daeacf7557bcba80ee34a9b22036bd2f5294540cb2e5e84fc1edac42211",
                    "verification": "2103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
                }
            ]
        }
    }
}
```

