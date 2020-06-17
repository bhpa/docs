# scripttoaddress方法

返回script_hash对应的地址

## 参数说明

- script_hash：地址散列值

  

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "scripttoaddress",
  "params": ["0x123efbc6137973683c140ab0e9a104e466173990"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script_hash": "0x123efbc6137973683c140ab0e9a104e466173990",
        "address": "AUvTLuKXk4tQGcwdxfoT9JhTy6bLFDhweG"
    }
}
```

