# showgas方法

返回本钱包的BhpGas。

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
  "method": "showgas",
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
        "unavailable": "1.3",
        "available": "0"
    }
}
```

响应说明：

- unavailable：不可用的BhpGas
- available：可用的BhpGas