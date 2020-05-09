# sendinvokescript 方法

根据参数构造合约交易并上链。

>  [!Note]
>
>   执行此命令前需要在 BHP-CLI 节点中打开钱包。

## 参数说明

- script：一个由虚拟机运行的脚本，与 InvocationTransaction 中携带的脚本相同。可通过 invoke、invokefunction、invokescript 获得。
- gas_consumed：执行此脚本需要的 GAS 费用。可通过 invoke、invokefunction、invokescript 获得。
- check_witness_address：可选，见证者的地址脚本，将从此地址收取手续费。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "sendinvokescript",
  "params": ["00c1046e616d6567d486f600d8d2456eb82c7a39d3019e02e5454104","0.043"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x793fb40fa55e5755779a0fe0267d80d8f7673b2503679153e92fd2e9cc3cd430",
        "size": 62,
        "type": "InvocationTransaction",
        "version": 1,
        "attributes": [
            {
                "usage": "Remark",
                "data": "3230323030353039303831303034373438a9d7eae47b31ba8b"
            }
        ],
        "vin": [],
        "vout": [],
        "sys_fee": "0",
        "net_fee": "0",
        "tx_fee": "0",
        "scripts": [],
        "script": "00c1046e616d6567d486f600d8d2456eb82c7a39d3019e02e5454104",
        "gas": "0"
    }
}
```

