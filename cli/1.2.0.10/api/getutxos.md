# getutxos方法

查询指定地址的未花费UTXO。

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- address：要查询UTXO的地址，该地址需为标准地址。

- asset_id：可选参数，资产 ID（资产标识符），即该资产在注册时的交易 ID，默认未BHP资产。

  资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getutxos",
  "params": ["AJQ6mhziuS5nYMTBVcu3egXkYtkYsKgcwZ"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "utxos": [
            {
                "txid": "0x04703605ca4932e4aca79b9a17a431907c69ab6c05a34be0f7c739ed0471bf7a",
                "vout": 2
            }
        ]
    }
}
```

响应说明：

- txid：该utxo所在的交易ID
- vout：该utxo在该交易中的索引