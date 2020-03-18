# sendrawtransaction方法

广播交易

## 参数说明

hex：在程序中构造的已签名的交易序列化后的 16 进制字符串

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "sendrawtransaction",
  "params": ["80000001914c540e0fcec3b54b6aa140cf1cdd62b4388fcf89b17d47ee5fbdeea1a8541f02000220f548f1fbf82121e2bd2f5d1c909f8ed44c81ff9392a56f82db75c32f6f6ace40420f0000000000c4b971c3838b81d744d9931ebe21fe81e0ab8e3c20f548f1fbf82121e2bd2f5d1c909f8ed44c81ff9392a56f82db75c32f6f6ace0053ecf9f25a00005e817ddca3dfe5ddf573c72f38e45fd9d0c74df7014140630816bb8eb583bfefc74a51afc7a2eb3cc987f7a55f4f396e00474ebc7f4fa5133f532fac30046f692a7b78decbe1c7ddf399c765ef69dd5b11857a63baa2b4232103e676e0bcaccb1fa3c0188aa5a608804cac5674d6933198cc59394125e5c243b6ac"],
  "id": 1
}
```

响应正文：

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

响应说明：

- 当 result 为 true 时表明当前交易广播成功
- 当 result 为 false 时表示当前交易广播失败，原因可能有双重花费、签名不完整等
- 本示例中广播了一个已经确认的交易，因为双重花费所以广播失败