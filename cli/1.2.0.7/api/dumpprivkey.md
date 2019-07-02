# dumpprivkey方法

导出指定地址的私钥

**执行此命令前需要在打开钱包**

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

address：要导出私钥的地址，该地址需为标准地址。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "dumpprivkey",
  "params": ["AJQ6mhziuS5nYMTBVcu3egXkYtkYsKgcwZ"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "L3XNav******************************wCwftN"
}
```

响应说明：

返回该标准地址的私钥。