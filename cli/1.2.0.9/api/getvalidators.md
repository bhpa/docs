# getvalidators方法

获取当前BHP共识节点的信息及投票情况

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getvalidators",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        {
            "publickey": "03e6f7b3b8c322ba7c47cd120327333e04fe50697bd36912889d265fc7f6ee81ad",
            "votes": "46632420",
            "active": true
        }
        ......
    ]
}
```

响应说明：

- publickey: 候选人公钥
- votes: 候选人所得票数
- active: true 表示该候选人已经成为共识节点，反之，false 表示该候选人未成为共识节点