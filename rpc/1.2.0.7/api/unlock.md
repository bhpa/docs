# unlock方法

将钱包解锁指定时长，单位秒。

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- password：打开钱包的密码。
- seconds ：解锁钱包的秒数，600=10分钟。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "unlock",
  "params": ["your password", 60],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "true"
}
```

