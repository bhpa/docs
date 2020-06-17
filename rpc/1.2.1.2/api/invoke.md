# invoke方法

使用给定的参数以散列值调用智能合约，并返回结果

>  [!Note]
>
>   此方法用于测试你的虚拟机脚本，如同在区块链上运行一样。这个 RPC 调用对区块链没有任何影响
>

## 参数说明

- scripthash：智能合约脚本散列值
- params：传递给智能合约的参数
- checkWitnessHash：可选，见证者的地址脚本

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "invoke",
  "params": [
  	"0xc81d3eb085e4423ff355328a22970e1fdbe9de2b",
  	[
  		{
  			"type": "String",
    		"value": "name"
    	},
		{
			"type":"Boolean",
		    "value": false
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

