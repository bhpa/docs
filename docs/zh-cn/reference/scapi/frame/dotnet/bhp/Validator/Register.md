# Validator.Register 方法 (byte[])

报名成为记账人，仅是报名操作，能否当选需要其它 BHP 持有人的投票。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern Neo.SmartContract.Framework.Services.Neo.Validator Register(byte[] pubkey)
```

参数：

pubkey：公钥，长度为33的字节数组。

返回值：[Validator](../Validator.md) 类型。

## 示例

```c#
public class Contract1 : FunctionCode
{
    public static void Main()
    {
        byte[] pubKey = new byte[] { 3,133,91,111,15,116,128,114,208,206,218,240,72,231,208,214,204,76,231,5,217,231,148,12,191,41,14,89,253,94,193,58,164 };
        var result = Validator.Register(pubKey);
    }
}
```



[返回上级](../Validator.md)