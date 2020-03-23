# UTXO模型

与账户余额模型不同的是，UTXO（Unspent Transaction Output）模型并不直接记录账户资产，而是通过未花费的`output`计算用户资产。每一笔 UTXO 类型的资产（如全局资产)，都是`input-output`关联模型，`input`指明了资金来源，`output`指明了所有资产的去向。

> [!WARNING]
>
> - 当交易有手续费时，input.GAS > output.GAS
> - 当持有 BHP 提取GAS分红时 input.GAS < output.GAS
> - 当发行资产时，input.Asset < output. Asset

UTXO 转账其实是对能解锁`Output.scriptHash`的 output 进行消费，并在新交易的见证人上填充其签名参数。账户地址，实际上就是脚本 hash 的 base58check 处理，代表的是一段签名认证脚本，如下图。 

[`Op.CheckSig`](../neo_vm.md#checksig) 执行时需要公钥和签名两个参数，在地址脚本中，已经包含公钥参数，故在交易中只需要补充签名参数。

![utxo](../../../assets\utxo.png)
