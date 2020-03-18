# getcontractstate方法

根据合约脚本散列，查询合约信息

## 参数说明

script_hash：合约脚本散列

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getcontractstate",
  "params": ["0x40361b2537865ebc0284e623f2825af25ef5bd8f"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "version": 0,
        "hash": "0x40361b2537865ebc0284e623f2825af25ef5bd8f",
        "script": "00c56b51616c7566",
        "parameters": [
            "Void"
        ],
        "returntype": "Boolean",
        "name": "1",
        "code_version": "1",
        "author": "1",
        "email": "1",
        "description": "1",
        "properties": {
            "storage": true,
            "dynamic_invoke": true
        }
    }
}
```

