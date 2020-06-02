# 大小端序的使用

 BHP 系统中所有的整数类型都是采用小端序 (Little Endian) 编码，只有在传输 IP 地址和端口号采用大端序 (Big Endian) 编码。

开发者在实际使用过程中，特别是通过SDK构造交易来转账或者调用合约的时候，需要正确使用钱包地址 ScriptHash 的大小端序格式，否则可能导致全局资产或者 BRC20 资产的丢失。

本文将结合几个常见的应用场景，介绍如何正确使用钱包地址或者合约 ScriptHash 的字节序格式。

## 地址和 ScriptHash
### 钱包地址的ScriptHash
在 BHP 区块链中创建钱包时都会生成私钥、公钥、钱包地址以及对应的 ScriptHash。

以下是一个钱包的标准地址和 ScriptHash 大小端序的示例： 

- 地址 (address): ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy
- ScriptHash
  - 大端序：0x 51afd1c72987b773049414c1f96c6b83d4977c6f
  - 小端序：6f7c97d4836b6cf9c114940473b78729c7d1af51

要进行钱包地址与 ScriptHash 的互转，以及 ScriptHash 的大小端序之间的互转，可以使用以下一种方法:

- BHP SDK，详情请参见 [常见数据类型转换](../sdk/conversion.md)

### 合约的ScriptHash
每一个合约部署成功后，会生成一个 ScriptHash 作为该合约的唯一标识符。BHP 的合约对应的 ScriptHash 可以转换为 20 个字节的标准地址，用来接收全局资产或者 BRC20 资产。这种情况下合约的 ScriptHash 作为大端序使用，例如：

- CGas ScriptHash (大端序)：0x 51afd1c72987b773049414c1f96c6b83d4977c6f

- CGas合约对应的地址：ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy

## 大小端序使用场景
钱包地址的使用常见于全局资产转账交易和智能合约调用，这里我们主要针对这两个场景来介绍如何使用地址ScriptHash的字节序格式。
### 全局资产转账交易
当使用 BHP SDK 构造全局资产转账交易(ContractTransaction)时, 需要为转账资产的接收人构造相应的 Output。如下所示，需要在 TransactionOutput 中填写资产接收人的钱包地址所对应的 ScriptHash , 这里应该使用**大端序**的格式：

```
var outputs = new List<TransactionOutput>{ new TransactionOutput()
{
    AssetId = Blockchain.UtilityToken.Hash, //GAS对应的AssetId
    ScriptHash = "ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy".ToScriptHash(), //地址对应的大端序 ScriptHash
    Value = new Fixed8((long)(0.999 * (long)Math.Pow(10, 8)))
}}.ToArray();
```

### 智能合约调用
在调用智能合约时，有的场景下需要传入钱包地址对应的 ScriptHash，这时要注意使用正确的大小端序格式。

#### 通过RPC接口调用合约

这里以 [InvokeFunction](../../reference/rpc/api/invokefunction.md) 为例，调用 BRC20 合约的 balanceOf 方法。

如果传入的地址，参数类型为 Hash160，需要使用**大端序**的地址 ScriptHash。

```
    {
        "jsonrpc": "2.0",
        "method": "invokefunction",
        "params": [
            "74f2dc36a68fdc4682034178eb2220729231db76",
            "balanceOf",
            [
            {
                "type": "Hash160", //数据类型使用Hash160
                "value": "51afd1c72987b773049414c1f96c6b83d4977c6f" //地址ScriptHash为大端序
            }
            ]
        ],
        "id": 3
    }
```

如果参数类型为ByteArray，需要使用**小端序**的地址ScriptHash。

```
{
    "jsonrpc": "2.0",
    "method": "invokefunction",
    "params": [
        "74f2dc36a68fdc4682034178eb2220729231db76",
        "balanceOf",
        [
        {
            "type": "ByteArray", //数据类型ByteArray
            "value": "6f7c97d4836b6cf9c114940473b78729c7d1af51" //地址ScriptHash为小端序
        }
        ]
    ],
    "id": 3
}
```

#### 通过SDK构造调用合约的交易

如果使用 BHP SDK 构造 InvocationTransaction，调用合约的执行脚本需要通过 ScriptBuilder 构造，这时应该使用**小端序**的地址 ScriptHash 作为参数。

合约执行完成后，可以通过 [getapplicationlog 方法](../../reference/rpc/api/getapplicationlog.md) 查看执行日志，执行日志在输出地址的时候，是以 ByteArray 为数据类型，输出地址相对应的小端序 ScriptHash。

