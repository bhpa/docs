# gettransactiondata方法

获取交易的的十六进制字符串

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- asset_id：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过 CLI 命令 中的 list asset 命令查询，也可以在区块链浏览器中查询。
- address：收款地址（sendtoaddress使用）
- value：转账金额
- fee：手续费，可选参数，默认为 0
- change_address：找零地址，可选参数，默认为钱包中第一个标准地址
- fee_address：bhp手续费地址，可选参数。（转账资产为BHP时，此参数无效）

## 调用示例

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "gettransactiondata",
  "params": ["0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",1.2,"ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "8000000299f46ee7285a4080518a83ffbbf265b865cfb02c5c14759f4deeef85676c6612010062b3d6e8123e72a5859e87e65aea90bc7a4018fcc53b090f95658f41c7067cf601000354a80a4c72f6157a7af0a753fc4ac4af6b159a17634dd57fecf319feab6ff713000e2707000000008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc54a80a4c72f6157a7af0a753fc4ac4af6b159a17634dd57fecf319feab6ff713d9dc1101000000008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc2512753e7083dbfc9308c4abcaf55bbb0bd9b429a1a579312e02502bbb5d0ba654b8a405000000008226c513e2aa717f2f32d3c5fb2bcb492acfc3dc014140df5220a557f83f086d0da245497384810803f192b2958b53309e3fd7aa0e3a98437c5554a6d4417a448466f74bd3c6d0a4aefc17da54b70dcd87afb13c337682232103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
}
```

