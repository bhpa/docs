# submitblock方法

在 BHP 网络广播原始区块。

## 参数说明

Hex: 序列化区块的十六进制字符串。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "submitblock",
  "params": ["000000000000000000000000000000000000000000000000000000000000000000000000845c34e7c1aed302b1718e914da0c42bf47c476ac4d89671f278d8ab6d27aa3d65fc8857000000001dac2b7c00000000be48d3a3f5d10013ab9ffee489706078714f1ea2010001510400001dac2b7c00000000400000455b7b226c616e67223a227a682d434e222c226e616d65223a22e5b08fe89a81e882a1227d2c7b226c616e67223a22656e222c226e616d65223a22416e745368617265227d5d0000c16ff28623000000da1745e9b549bd0bfa1a569971c77eba30cd5a4b00000000400001445b7b226c616e67223a227a682d434e222c226e616d65223a22e5b08fe89a81e5b881227d2c7b226c616e67223a22656e222c226e616d65223a22416e74436f696e227d5d0000c16ff286230008009f7fd096d37ed2c0e3f7f0cfc924beef4ffceb680000000001000000019b7cffdaa674beae0f930ebe6085af9093e5fe56b34a5c220ccdcf6efc336fc50000c16ff2862300be48d3a3f5d10013ab9ffee489706078714f1ea201000151"],
  "id": 1
}
```

响应正文：

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

失败的响应正文:

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "error": {
        "code": -501,
        "message": "Block or transaction already exists and cannot be sent repeatedly."
    }
}
```

响应说明：

当结果为 false 时，区块广播失败并引发异常。可能返回以下错误代码：

| 错误码 | 消息                                                         |
| ------ | ------------------------------------------------------------ |
| -501   | Block or transaction already exists and cannot be sent repeatedly. |
| -502   | The memory pool is full and no more transactions can be sent. |
| -503   | The block cannot be validated.                               |
| -504   | Block or transaction validation failed.                      |
| -505   | One of the Policy filters failed.                            |
| -500   | Unknown error.                                               |
