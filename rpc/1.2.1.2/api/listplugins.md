# listplugins 方法

显示节点已加载的插件列表。

## 参数说明

无

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "listplugins",
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
            "name": "ApplicationLogs",
            "version": "1.2.1.1",
            "interfaces": [
                "IRpcPlugin",
                "IPersistencePlugin"
            ]
        }
        ......
    ]
}
```
