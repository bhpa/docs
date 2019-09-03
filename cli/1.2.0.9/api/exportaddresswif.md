# exportaddresswif方法

获取指定地址的信息

>  [!Note] 执行此命令前需要在 Bhp-CLI 节点中打开钱包。

## 参数说明

- address：要转账的地址，该地址需为标准地址。

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "exportaddresswif",
  "params": ["AFn2VfsXCC77qRgwAHUtU6oDgFktVoXfSj"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "wif": "L171n9yN****************5st9NyLa9",
        "prikey": "73e79292*************27b5ec",
        "pubkey": "02023ceab8b8388bab78637dd1492d51eb00cae0bc3c1b770b365d33dd1003e952",
        "address": "AFn2VfsXCC77qRgwAHUtU6oDgFktVoXfSj"
    }
}
```

响应说明：

- wif：该标准地址私钥的WIF格式
- prikey：该标准地址的私钥
- pubkey：该标准地址的公钥
- address：该标准地址的私钥