# invokefunction方法

使用给定的操作和参数，以散列值调用智能合约之后返回结果

>  [!Note] 此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个RPC调用对区块链没有任何影响。

## 参数说明

- scripthash：智能合约脚本散列值
- operation：操作名称（字符串）
- params：传递给智能合约操作的参数

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "invokefunction",
  "params": [
    "8226c513e2aa717f2f32d3c5fb2bcb492acfc3dc",
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
        "tx": "d1012000c108646563696d616c7367be39e7b562f60cbfe2aebca375a2e5ee28737caf000000000000000000000000"
    }
}
```

