# 常用数据类型转换

### 16 进制字符串与 byte 数组互转

```c#
//16进制字符串转Byte数组
string pubkey = "03705ff82d610058bb8186796d3f9210c68d0cac81ab167cd69946c447f5ef4764";
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
UInt160 scriptHash = "ARwMufsDMXFDvtCH9cpjxUHD1pBsZvRkJy".ToScriptHash();
string address = scriptHash.ToAddress();
```

如果 Script Hash 是大端序的字符串格式，可以用下面的方法转成 Address：

```c#
string address = new UInt160("0x51afd1c72987b773049414c1f96c6b83d4977c6f".Remove(0, 2).HexToBytes().Reverse().ToArray()).ToAddress();
```

### 大端序与小端序互转

```c#
//big-endian 2 little-endian
Console.WriteLine("0x6f7c97d4836b6cf9c114940473b78729c7d1af51".Remove(0, 2).HexToBytes().Reverse().ToHexString());
//little-endian 2 big-endian
Console.WriteLine("0x" + "51afd1c72987b773049414c1f96c6b83d4977c6f".HexToBytes().Reverse().ToHexString());
```

### 16 进制字符与 BigInteger 互转

```c#
BigInteter bigInt = new BigInteger("00e1f505".HexToBytes());
string hexStr = new BigInteger(100000000).ToByteArray().ToHexString();
```

## 期待更多
更多 BHP SDK 用法正在补充中。
