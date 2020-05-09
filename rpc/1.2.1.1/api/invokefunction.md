# invokefunction方法

使用给定的操作和参数，以散列值调用智能合约之后返回结果

>  [!Note]
>
>   此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个 RPC 调用对区块链没有任何影响。
>

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
    "0xc81d3eb085e4423ff355328a22970e1fdbe9de2b",
    "balanceOf",
    [
      {
        "type": "Hash160",
        "value": "0xdcc3cf2a49cb2bfbc5d3322f7f71aae213c52682"
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
        "script": "148226c513e2aa717f2f32d3c5fb2bcb492acfc3dc51c10962616c616e63654f66672bdee9db1f0e97228a3255f33f42e485b03e1dc8",
        "state": "HALT, BREAK",
        "gas_consumed": "0.226",
        "stack": [
            {
                "type": "ByteArray",
                "value": ""
            }
        ],
        "notifications": []
    }
}
```

