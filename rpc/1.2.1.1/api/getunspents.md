# getunspents 方法

返回指定账户中未花费的 UTXO 资产（如 BHP、GAS）信息。

> 此方法由插件提供，需要安装 [RpcSystemAssetTracker](https://github.com/BhpAlpha/bhp-plugins/releases) 插件才可以调用。

## 参数说明

- address ：指定要查询的账户地址。
- asset_id：资产 ID（资产标识符），即该资产在注册时的交易 ID。其余资产 ID 可以通过 CLI 命令 中的 `list asset` 命令查询，也可以在区块链浏览器中查询。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getunspents",
  "params": ["0x51afd1c72987b773049414c1f96c6b83d4977c6f","0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854"],
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
                "unspent": [
                    {
                        "txid": "98ba965e6f65b8ed774e99b1c6e931821a80fb2bc9476ca9696c4196f589a0b6",
                        "n": 0,
                        "value": 44999999.9995
                    }
                ],
                "asset_hash": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "amount": 44999999.9995
            }
        ],
        "address": "ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy"
    }
}
```
