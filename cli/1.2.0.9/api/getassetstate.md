# getassetstate方法

根据指定的资产编号，查询资产信息

## 参数说明

asset_id：资产 ID（资产标识符），即该资产在注册时的交易 ID。

资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getassetstate",
  "params": ["0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "version": 0,
        "id": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
        "type": "GoverningToken",
        "name": [
            {
                "lang": "zh-CN",
                "name": "算力币"
            },
            {
                "lang": "en",
                "name": "BHP"
            }
        ],
        "amount": "45000000",
        "available": "45000000",
        "precision": 8,
        "owner": "00",
        "admin": "Abf2qMs1pzQb8kYk9RuxtUb9jtRKJVuBJt",
        "issuer": "Abf2qMs1pzQb8kYk9RuxtUb9jtRKJVuBJt",
        "expiration": 4000000,
        "frozen": false
    }
}
```
