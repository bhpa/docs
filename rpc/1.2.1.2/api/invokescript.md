# invokescript方法

通过虚拟机传递脚本之后返回结果。

>  [!Note] 
>
>  此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个 RPC 调用对区块链没有任何影响。
>

## 参数说明

script：一个由虚拟机运行的脚本，与 InvocationTransaction 中携带的脚本相同

checkWitnessHash：可选，见证者的地址脚本

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "invokescript",
  "params": ["00046e616d65672bdee9db1f0e97228a3255f33f42e485b03e1dc8"],
  "id": 3
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "script": "00046e616d65672bdee9db1f0e97228a3255f33f42e485b03e1dc8",
        "state": "HALT, BREAK",
        "gas_consumed": "0.06",
        "stack": [
            {
                "type": "ByteArray",
                "value": "4d794252433230"
            }
        ],
        "notifications": []
    }
}
```

