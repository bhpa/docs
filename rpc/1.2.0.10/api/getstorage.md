# getstorage方法

根据合约脚本散列和存储的 key，返回存储的 value

## 参数说明

- script_hash: 合约脚本散列。
- key: 存储区的键。（需要转化为hex string）

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getstorage",
  "params": ["03febccf81ac85e3d795bc5cbd4e84e907812aa3", "5065746572"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "4c696e"
}
```

