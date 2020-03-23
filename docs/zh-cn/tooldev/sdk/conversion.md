# 常用数据类型转换

### 16 进制字符串与 byte 数组互转

```c#
//16进制字符串转Byte数组
string pubkey = "020a2a4f2ef618d7d38606c2a65ff941b8898d00cdade6e4ed2437052cffde16d2";
var bytes = pubkey.HexToBytes();
//Byte数组转16进制字符串
string pubkey2 = bytes.ToHexString();
Console.WriteLine(pubkey2);
```

### DateTime 与 Unix 时间戳互转

```c#
//DateTime转Unix时间戳
DateTime date = new DateTime(2018,8,8,8,8,8);
uint timestamp = date.ToTimestamp();
//Unix时间戳转DateTime
DateTime date2 = timestamp.ToDateTime();
Console.WriteLine(date2.ToString());
```

### Address 与 Script Hash 互转

```c#
UInt160 scriptHash = "AXfgAN3coFD1LXbAyCnnMS8LmmSNVrJCt9".ToScriptHash();
string address = scriptHash.ToAddress();
```

如果 Script Hash 是大端序的字符串格式，可以用下面的方法转成 Address：

```c#
string address = new UInt160("0xedf0b786bf74dd09372cd006ef55eb73e82f5cbb".Remove(0, 2).HexToBytes().Reverse().ToArray()).ToAddress();
```

### 大端序与小端序互转

```c#
//big-endian 2 little-endian
Console.WriteLine("0xedf0b786bf74dd09372cd006ef55eb73e82f5cbb".Remove(0, 2).HexToBytes().Reverse().ToHexString());
//little-endian 2 big-endian
Console.WriteLine("0x" + "bb5c2fe873eb55ef06d02c3709dd74bf86b7f0ed".HexToBytes().Reverse().ToHexString());
```

### 16 进制字符与 BigInteger 互转

```c#
BigInteter bigInt = new BigInteger("00e1f505".HexToBytes());
string hexStr = new BigInteger(100000000).ToByteArray().ToHexString();
```

## 期待更多
更多 BHP SDK 用法正在补充中。
