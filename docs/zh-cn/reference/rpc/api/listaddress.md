# listaddress方法

列出当前钱包内的所有地址。

>  [!Note]
>
>   执行此命令前需要在 BHP-CLI 节点中打开钱包。

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "listaddress",
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
            "address": "AJQ6mhziuS5nYMTBVcu3egXkYtkYsKgcwZ",
            "haskey": true,
            "label": null,
            "watchonly": false
        }
    ]
}
```

响应说明：

- address：钱包内的地址
- watchonly：该地址是否为监视地址