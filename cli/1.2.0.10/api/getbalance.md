# getbalance方法

根据指定的资产编号，返回钱包中对应资产的余额信息

> - 执行此命令前需要在 Bhp-CLI 节点中打开钱包
> - 全局资产查询：当区块未完全同步时，返回的资产余额可能不是最新的，请确保使用该 API 时区块已经同步到最新高度。
> - 合约资产查询：a. 当未同步到发布合约的区块时，执行该 API 会报错，只有当区块同步到发布该合约资产的区块时，才会返回正确的结果。b. 当区块未完全同步时，返回的资产余额可能不是最新的，请确保使用该 API 时区块已经同步到最新高度。

## 参数说明

asset_id：资产 ID（资产标识符），如果是全局资产，此处为注册资产时的 Register Transaction 或 Publish Transaction 的交易 ID，如果是合约内部资产，此处为合约的 Script Hash。资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getbalance",
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
        "balance": "0",
        "confirmed": "0"
    }
}
```

响应说明：

- balance：钱包中该资产的真实余额。
- confirmed：钱包中该资产的已确认的金额，只有已确认的金额可以用来转账。
- balance 和 confirmed 二者可能会不相等，仅在从钱包中转出一笔钱，而且有找零未确认时时，confirmed 值会小于balance。当这笔交易确定后，二者会变得相等。