# getpeers方法

获得该节点当前已连接/未连接的节点列表

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getpeers",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "unconnected": [        
            {
                "address": "47.103.46.191",
                "port": 20555
            }
        ],
        "bad": [],
        "connected": [
            {
                "address": "47.103.46.213",
                "port": 20555
            }
        ]
    }
}
```

响应说明：

- unconnected：当前未连接到的节点
- bad：不再连接（拉黑）的节点
- connected：当前已连接到的节点