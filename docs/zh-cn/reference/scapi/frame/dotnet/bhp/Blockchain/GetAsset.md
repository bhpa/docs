# Blockchain.GetAsset 方法 (byte[])

根据资产 ID，在区块链中查找该资产。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern Bhp.SmartContract.Framework.Services.Bhp.Asset GetAsset(byte[] asset_id)
```

参数：资产ID，32字节的字节数组。

返回值：资产，[Asset](../Asset.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        //以 BHP 资产为例
        byte[] asset = { 84,168,10,76,114,246,21,122,122,240,167,83,252,74,196,175,107,21,154,23,99,77,213,127,236,243,25,254,171,111,247,19 };
        Asset ass = Blockchain.GetAsset(asset); 
    }
}
```

其中 asset 可以在外部事先获得，也可以作为参数传入智能合约。下面是在外部代码中调用 SDK 将资产 ID 的 16 进制字符串转成 byte 数组。

```c#
static void Main(string[] args)
{
    byte[] asset = Bhp.Helper.HexToBytes("13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854");
}
```



[返回上级](../Blockchain.md)