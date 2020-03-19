# getwalletheight方法

获取当前钱包索引高度。

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getwalletheight",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": 952291
}
```

