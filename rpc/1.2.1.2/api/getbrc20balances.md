# getbrc20balances方法

返回指定地址内的所有 BRC-20 资产余额。

> 此方法由插件提供，需要安装 [RpcBrc20Tracker](https://github.com/BhpAlpha/bhp-plugins/releases) 插件才可以调用。

## 参数说明

address：账户地址。可以是 A 开头的 34 位长度的字符串，如 ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy。也可以是地址HASH，如 0x51afd1c72987b773049414c1f96c6b83d4977c6f。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getbrc20balances",
  "params": ["0x51afd1c72987b773049414c1f96c6b83d4977c6f"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "balance": [
            {
                "asset_hash": "fe4e30a20a71b0472b8a38cac0bd4fae4e38fb1a",
                "amount": "10000000000000000",
                "last_updated_block": 6213
            },
            {
                "asset_hash": "dc2a5ec514a6932fa98a76029f42c5326e15e6fc",
                "amount": "10000000000000000",
                "last_updated_block": 19091
            }
        ],
        "address": "ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy"
    }
}
```

> 当区块未完全同步时，返回的资产余额可能不是最新的，请确保使用该 API 时区块已经同步到最新高度。