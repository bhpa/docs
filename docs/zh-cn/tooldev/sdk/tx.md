# 构造交易

### 交易签名

```c#
private static Transaction SignWithWallet(Transaction tx)
{
    if (tx == null)
    {
        throw new ArgumentNullException("tx");
    }
    try
    {
        tx.ToJson();
    }
    catch (Exception)
    {
        throw new FormatException("交易格式错误");
    }

    var wallet = new BRC6Wallet(new WalletIndexer("Index_038263E2"), "1.json");
    try
    {
        wallet.Unlock("password");
    }
    catch (Exception)
    {
        Console.WriteLine("password error");
    }

    //Signature
    var context = new ContractParametersContext(tx);
    wallet.Sign(context);
    if (context.Completed)
    {
        Console.WriteLine("签名成功");
        tx.Witnesses = context.GetWitnesses();
    }
    else
    {
        Console.WriteLine("签名失败");
    }
    return tx;
}
```

### 验证交易

```c#
var system = new BhpSystem(new LevelDBStore("Chain_038263E2"));
var tx = makeTransaction(); //构造交易
tx.Verify(Blockchain.Singleton.GetSnapshot(), new List<Transaction> { tx });
```

### 支付网络手续费

支付手续费只需修改交易的 inputs 和 outputs。网络手续费 = inputs 中的 GAS - outputs 中的 GAS - 系统手续费。以下是支付 0.001 GAS 的简单示例。

```c#
//交易输入是 0.00102616 GAS
var inputs = new List<CoinReference> {
    new CoinReference(){
        PrevHash = new UInt256("0x8ed089097ecee8b00f2a860972fc02fdf750b275bb3be23b81e2c843fec7ec3b".Remove(0, 2).HexToBytes().Reverse().ToArray()),
        PrevIndex = 0
    }
}.ToArray();

//交易输出是 0.00002616 GAS，找回到原地址
var outputs = new List<TransactionOutput>{ new TransactionOutput()
{
    AssetId = Blockchain.UtilityToken.Hash,
    ScriptHash = "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY".ToScriptHash(),
    Value = new Fixed8((long)(0.00002616 * (long)Math.Pow(10, 8)))
}}.ToArray();

//则手续费是 0.001 GAS
```



更多常见用法正在补充中。
