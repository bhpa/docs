# validateaddress方法

验证地址是否是正确的BHP地址

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

address：地址

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "validateaddress",
  "params": ["AJQ6mhziuS5nYMTBVcu3egXkYtkYsKgcwZ"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "address": "AJQ6mhziuS5nYMTBVcu3egXkYtkYsKgcwZ",
        "isvalid": true
    }
}
```
