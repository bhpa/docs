# invokescript方法

通过虚拟机传递脚本之后返回结果。

>  [!Note] 
>
>  此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个 RPC 调用对区块链没有任何影响。
>
>  当钱包打开时，将返回交易脚本及交易ID。

## 参数说明

script：一个由虚拟机运行的脚本，与 InvocationTransaction 中携带的脚本相同

checkWitnessHash：可选，见证者的地址脚本

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "invokescript",
  "params": ["00046e616d6567a19fdec77a7510ea5bf99b8be58648bae734596a"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "00046e616d6567a19fdec77a7510ea5bf99b8be58648bae734596a",
        "state": "HALT, BREAK",
        "gas_consumed": "0.038",
        "stack": [
            {
                "type": "ByteArray",
                "value": "52555344"
            }
        ],
        "tx": "d1011b00046e6d1011b00046e616d6567a19fdec77a7510ea5bf99b8be58648bae734596a0000000000000000000154a8e0fd25a7f3f8af8bf0110bcd0f3aa9c57338998de83d2cbc5e926f5c6e0c0200012512753e7083dbfc9308c4abcaf55bbb0bd9b429a1a579312e02502bbb5d0ba6e05dd9867e0100008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc01414005b3cd19918e3a94cdf3413d471aa2c1e0b6c599ca9bd4c2c79a4f34be584e31ce5fc56cfc4469f8244ddfaa24e9da82127496f8ab8180ab823098bf9fbecc3f232103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac16d656724058e5e1b6008847cd662728549088a9ee82191000000000000000000000000",
        "txid": "0xcbfcd24a3e1ffcdd5b6f045e0c9a6afefb0f0e8b2e02e0beef1b4c40f67f12d9"
    }
}
```

