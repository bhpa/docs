# invokefunction方法

使用给定的操作和参数，以散列值调用智能合约之后返回结果

>  [!Note]
>
>   此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个 RPC 调用对区块链没有任何影响。
>
>  当钱包打开时，将返回交易脚本及交易ID。

## 参数说明

- scripthash：智能合约脚本散列值
- operation：操作名称（字符串）
- params：传递给智能合约操作的参数
- checkWitnessHash：可选，见证者的地址脚本

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "invokefunction",
  "params": [
    "6a5934e7ba4886e58b9bf95bea10757ac7de9fa1",
    "balanceof",
    [
      {
        "type": "Hash160",
        "value": "dcc3cf2a49cb2bfbc5d3322f7f71aae213c52682"
      }
    ]
  ],
  "id": 3
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "script": "00c108646563696d616c7367be39e7b562f60cbfe2aebca375a2e5ee28737caf",
        "state": "HALT, BREAK",
        "gas_consumed": "0.174",
        "stack": [
            {
                "type": "Integer",
                "value": "8"
            }
        ],
        "tx": "d1011b00046e616d6567a19fdec77a7510ea5bf99b8be58648bae734596a0000000000000000000154a8e0fd25a7f3f8af8bf0110bcd0f3aa9c57338998de83d2cbc5e926f5c6e0c0200012512753e7083dbfc9308c4abcaf55bbb0bd9b429a1a579312e02502bbb5d0ba6e05dd9867e0100008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc01414005b3cd19918e3a94cdf3413d471aa2c1e0b6c599ca9bd4c2c79a4f34be584e31ce5fc56cfc4469f8244ddfaa24e9da82127496f8ab8180ab823098bf9fbecc3f232103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac",
        "txid": "0xcbfcd24a3e1ffcdd5b6f045e0c9a6afefb0f0e8b2e02e0beef1b4c40f67f12d9"
    }
}
```

