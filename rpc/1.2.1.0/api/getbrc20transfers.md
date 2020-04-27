# getbrc20transfers方法

返回指定地址内的所有 BRC-20 交易记录。

> 此方法由插件提供，需要安装 [RpcBrc20Tracker](https://github.com/BhpAlpha/bhp-plugins/releases) 插件才可以调用。

## 参数说明

- address：账户地址。可以是 A 开头的 34 位长度的字符串，如 ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy。也可以是地址HASH，如 0x51afd1c72987b773049414c1f96c6b83d4977c6f。
- timestamp (可选)：
  - 如果设置起始和结束时间戳，则返回时间戳范围内的交易信息。
  - 如果仅设置一个时间戳，则返回自该时间戳以后发生的交易信息。
  - 如果不设置此参数，则返回近七天内的交易信息。



## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getbrc20transfers",
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
        "sent": [
            {
                "timestamp": 1587952230,
                "asset_hash": "c81d3eb085e4423ff355328a22970e1fdbe9de2b",
                "transfer_address": "ASQEcuGABdnPsUGFyRQzVYcApYpFhGEZNc",
                "amount": "2",
                "block_index": 40153,
                "transfer_notify_index": 0,
                "tx_hash": "939e4918968604cc83a54b4c443108a0cea043669994f0bac77777b1c3510945"
            }
        ],
        "received": [
            {
                "timestamp": 1587951671,
                "asset_hash": "c81d3eb085e4423ff355328a22970e1fdbe9de2b",
                "transfer_address": "AFmseVrdL9f9oyCzZefL9tG6UbvhPbdYzM",
                "amount": "10000000000000000",
                "block_index": 40069,
                "transfer_notify_index": 0,
                "tx_hash": "d7d5ca0549f258cb718e49aa4c8daddc926252025c13c400d09843effbcc169d"
            }
        ],
        "address": "ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy"
    }
}
```

