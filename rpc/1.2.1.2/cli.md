# CLI 命令参考

> 修改
>
> - install 允许在线安装插件
> - import multisigaddress
> 

打开命令行，定位到 BHP-CLI 所在目录，输入以下命令即可启动 BHP 的命令行钱包。

`dotnet bhp-cli.dll`

本节将介绍命令行钱包的所有命令，你可以通过输入命令的形式操作钱包，如创建打开钱包、导入导出私钥、转账、启动共识等。

## 命令概览

以下表格列出了所有 CLI 命令。在命令行中输入 `help` 也可以查看所有命令。

本文中的命令格式均遵循以下约定：

- `<>` ：表示参数
- `[]` ：可选参数
- `|` ：表示所填的参数可以是其中任意一种
- `=` ：表示可选参数在不输入情况下的默认值

### 合约命令 

| 命令              | 参数                                                         | 说明     |
| ----------------- | ------------------------------------------------------------ | -------- |
| [deploy](#deploy) | \<avmFilePath>\<paramTypes> \<returnTypeHexString> \<hasStorage (true\|false)> <hasDynamicInvoke (true\|false)> <isPayable (true\|false)>\<contractName> \<contractVersion>\<contractAuthor> \<contractEmail> \<contractDescription> | 发布合约 |

### 控制台指令

| 命令               | 功能说明                               |
| ------------------ | -------------------------------------- |
| version            | 显示当前软件的版本                     |
| help [plugin-name] | 帮助菜单，也可以查看部分插件的提示信息 |
| clear              | 清除屏幕                               |
| exit               | 退出程序                               |

### 钱包命令

| 命令                                             | 参数                                       | 说明                                                         |
| ------------------------------------------------ | ------------------------------------------ | ------------------------------------------------------------ |
| [create wallet](#create wallet)                  | \<path>                                    | 创建钱包文件                                                 |
| [open wallet](#open wallet)                      | \<path>                                    | 打开钱包文件                                                 |
| close wallet                                     |                                            | 关闭钱包文件                                                 |
| [upgrade wallet](#upgrade wallet)                | \<path>                                    | 升级旧版钱包文件                                             |
| [rebuild index](#rebuild index)                  |                                            | 重建钱包索引。<br/>需要打开钱包。                            |
| list address                                     |                                            | 列出钱包中的所有账户<br/>需要打开钱包。                      |
| list asset                                       |                                            | 列出钱包中的所有资产<br/>需要打开钱包。                      |
| list key                                         |                                            | 列出钱包中的所有公钥<br/>需要打开钱包。                      |
| [show utxo](#show utxo)                          | [id\|alias]                                | 列出钱包中指定资产的 UTXO<br/>需要打开钱包。                 |
| [show gas](#show gas)                            |                                            | 列出钱包中的所有可提取及不可提取的 GAS<br/>需要打开钱包。    |
| [claim gas](#claim gas)                          | [all]\[changeAddress]                      | 提取钱包中可提取状态的 GAS（前50个地址或所有地址）<br/>需要打开钱包。 |
| [create address](#create address)                | [n为正整数，不填默认为1]                   | 创建地址 / 批量创建地址<br/>需要打开钱包。                   |
| [import key](#import key)                        | <wif\|path>                                | 导入私钥 / 批量导入私钥<br/>需要打开钱包。                   |
| [export key](#export key)                        | [address]\[path]                           | 导出私钥<br/>需要打开钱包。                                  |
| [export wallet](#export wallet)                  | \<path>                                    | 导出钱包信息<br/>需要打开钱包。                              |
| [import multisigadress](#import multisigaddress) | <m pubkeys>                                | 创建多方签名合约<br/>需要打开钱包。                          |
| [send](#send)                                    | <id\|alias>\<address>\<value>\|all [fee=0] | 向指定地址转账<br/>参数分别为：资产 ID，对方地址，转账金额，手续费<br/>需要打开钱包。 |
| [sign](#sign)                                    | \<jsonObjectToSign>                        | 签名<br/>参数：记录交易内容的 json 字符串<br/>需要打开钱包。 |

### 节点命令

| 命令            | 参数                | 功能说明                                       |
| --------------- | ------------------- | ---------------------------------------------- |
| show state      |                     | 显示当前区块链同步状态                         |
| show pool       | [verbose]           | 显示内存池中的交易（这些交易处于零确认的状态） |
| [relay](#relay) | \<jsonObjectToSign> | 广播<br/>参数：记录交易内容的 json 字符串      |

#### 插件命令

| 命令                | 参数             | 说明                                                         |
| ------------------- | ---------------- | ------------------------------------------------------------ |
| plugins             |                  | 显示已加载的插件                                             |
| [install](#install) | [Plugin name]    | 安装指定插件                                                 |
| uninstall           | [Plugin name]    | 卸载指定插件                                                 |
| export block[s]     | [path=chain.acc] | 导出全部区块数据，导出的结果可以用作离线同步                 |
| export block        | \<start> [count] | 从指定区块高度导出指定数量的区块数据，导出的结果可以用作离线同步 |

#### 高级命令

| 命令            | 说明     |
| --------------- | -------- |
| start consensus | 启动共识 |

## 命令说明

### deploy



将智能合约发布到链上。

##### 句法 

```
deploy <avmFilePath><paramTypes><returnTypeHexString><hasStorage(true|false)> <hasDynamicInvoke(true|false)><isPayable(true|false)><contractName><contractVersion><contractAuthor><contractEmail><contractDescription>
```

##### 参数 

- avmFilePath：avm文件路径
- paramTypes：合约传入参数类型
- returnTypeHexString: 返回类型十六进制字符串
- hasStorage：是否分配存储区
- hasDynamicInvoke：是否动态调用
- isPayable:是否可接受资产
- contractName：合约名称
- contractVersion：合约版本
- contractAuthor:合约作者
- contractEmail:合约发布者邮箱
- contractDescription:合约描述

```

```

### create wallet

创建一个 .db3 或 .json 钱包文件。创建过程中需要设置钱包密码。

##### 句法

 `create wallet <path>` 

##### 示例

```
bhp> create wallet test.json
password: *
password: *
address: AcYUof1TBHUTMa1VKNKcBXSfK3NN8pXb49
pubkey: 03286bddc438b209ec979cfdf5cbf801ff072905cc651aba3ef5592349747bea61
```

创建的钱包文件存放在 BHP-CLI 根目录下，如果要指定其它路径，需要先创建好文件夹。

### open wallet

打开指定路径的钱包文件。打开钱包时需要输入钱包密码。

##### 句法

 `open wallet <path>` 

##### 示例

```
bhp> open wallet test.json
password: *
```

### upgrade wallet

升级旧版 .db3 钱包文件。

##### 句法

 `upgrade wallet <path>` 

##### 示例

```
bhp>upgrade wallet cli.db3
Wallet file upgrade complete. Old file has been auto-saved at: cli.old.db3
```

### rebuild index

重建钱包索引，此操作将强制钱包从区块高度为 0 开始同步区块交易。新创建的钱包不用重建钱包索引，只有要导入私钥或者钱包中资产显示异常时才需要重建钱包索引。

或者由于种种原因，钱包中的某笔交易未确认，这时资产已经从钱包中扣除，但并未经过整个区块链网络的确认。如果想删掉这笔未确认的交易使钱包中的资产正常显示也需要重建钱包索引。

### show utxo

列出钱包中指定资产的 UTXO。

##### 句法

`show utxo [id|alias]` 

##### 示例

```
bhp> show utxo
0x320066d51cd234a0acebbc93145a379105f45151d6380f3d15b6b8d9f9254d59:50
0x0c6e5c6f925ebc2c3de88d993873c5a93a0fcd0b11f08baff8f3a725fde0a854:2
total: 2 UTXOs
```

### show gas

列出当前钱包中的所有未提取的 GAS。

##### 句法

`show gas` 

##### 示例

```
unavailable: 3.3
  available: 2.1
```

其中 unavailable 表示不可提取的 GAS，available 表示可提取（待提取）的 GAS。

- 注：这里不包含已提取的 GAS，查看已提取的 GAS 请用 list asset 命令。

什么是可提取的 GAS，什么是不可提取的 GAS？

每一个 BHP 都有两种状态：unspent 和 spent。每一个未提取的 GAS 也有两种状态，available 和 unavailable。一个 BHP 的生命周期以转入地址起始，转出地址截止，转入时状态变为 unspent，转出时状态变为 spent。当 BHP 处于 unspent 状态时，所产生的 Gas 为 unavailable 状态，即不可提取。当 BHP 处于 spent 状态时，期间所产生的 GAS 变为 available，用户可以提取。

如何将钱包中的所有 unavailable GAS 转为 available GAS 呢，很简单，将钱包中的所有 BHP 转到钱包中的任意一个地址即可。

### claim gas

提取钱包中可提取状态下的 GAS，该过程是通过一个特殊的交易 Claim Transaction 完成的，输入命令后，客户端会输出 Claim Transaction 的 ID（提取 GAS 这笔交易的 ID）。

执行完 claim gas 命令后，再执行 list asset 会显示 GAS 有增加。

##### 句法

👉`claim gas [all] [changeAddress]`

##### 参数

`all`：提取钱包中所有地址的可提取状态的 GAS。如果不指定参数，则默认提取钱包前50个地址中的可提取状态的 GAS。

`changeAddress`：提取到指定地址。

### create address

在当前钱包中创建一个地址或批量创建地址。创建的地址会自动导出到程序目录下address+当前时间的文件中。

##### 句法

`create address [n]` 

##### 参数

`n`：要创建的地址数量。n 为正整数，不填默认为1

##### 示例

```
bhp> create address
[1/1]
export addresses to address20200413120126227.txt
```

### import key

导入一个私钥或者指定文件中的多个私钥。

##### 句法

 `import key <wif|path>`

##### 参数

`wif|path`：指定要导入的私钥，或者存放私钥的文件路径。

##### 示例

```
bhp> import key L4zRFphDJ******JT2EcmWPPpPH
address: AHYxZ6RkU7ZupZoJpESDtzD6WKoumqGNzw
pubkey: 03b2abff0998e53df0d80ff49c66653b588877c6e21046857384a35db2999b1f34
```

```
bhp> import key key.txt
```

### export key

导出地址对应的私钥到指定的文件。该命令需要验证钱包密码。

##### 句法

 `export key [address] [path]`

##### 参数

- `address`：指定要导出私钥的地址

- `path`：指定保存私钥的文件路径


##### 示例

将私钥输出到控制台：

```
bhp> export key
password: *
L3cZs25UoR******io286QKrQ
L5XogMXbdE******dTr65UWrA
L4zRFphDJp******EcmWPPpPH
```

```
bhp> export key AcYUof1TBHUTMa1VKNKcBXSfK3NN8pXb49
password: *
L3cZs25Uo******io286QKrQ
```

将私钥输出到指定文件中：

```
bhp> export key key1.txt
password: *
```

```
bhp> export key AcYUof1TBHUTMa1VKNKcBXSfK3NN8pXb49 key2.txt
password: *
```

### export wallet

导出钱包的相关信息到指定的文件，该命令需要验证钱包密码。

文件内容按`WIF 私钥 公钥 地址`排列，中间用空格间隔。

##### 句法

👉`export wallet <path>`

##### 参数

- `path`：导出的文件路径，如“D:\mywallet.txt"将导出到指定文件夹，或直接写文件名”mywallet.txt“则导出到程序目录下的该文件。

##### 示例

```
bhp> export wallet mywallet.txt
password: *
[4/4]
Export wallet to mywallet.txt success
```

### import multisigaddress

创建多方签名的合约地址。

##### 句法

`import multisigaddress m pubkeys...`

##### 参数

- `m`：以 m 个最小签名数量来创建多方签名的合约地址，例如两个公钥创建的多方签名地址， m 可以为 1 或 2
- `pubkeys`：创建多方签名合约地址的各方公钥

##### 示例

```
bhp> import multisigaddress 1 03286bddc438b209ec979cfdf5cbf801ff072905cc651aba3ef5592349747bea61 03b2abff0998e53df0d80ff49c66653b588877c6e21046857384a35db2999b1f34
Multisig. Addr.: AP8EDShPxWSvu7NXtLQfQCMWXnrkWFSADg
```

### send

向指定地址转账。该命令需要验证钱包密码。

##### 句法

`send <id|alias> <address> <amount>|all [fee=0]`

##### 参数

- `id|alias`：资产 ID 或资产缩写，如 bhp，gas
- `address`：收款地址
- `amount|all`：转账金额
- `fee`：设置手续费可以提升交易优先级，默认为0

##### 示例

将 100 GAS 转到地址 “AcYUof1TBHUTMa1VKNKcBXSfK3NN8pXb49”：

```
bhp> send 0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854 AcYUof1TBHUTMa1VKNKcBXSfK3NN8pXb49 100
password: *
TXID: 0x8f831d8de723093316c05749a053a226514bc06338b2bceb50db690610e0b92f
```

因为第二个参数除了资产 ID，还可以填写资产缩写，所以以上命令可以写成：

```
bhp> send bhp AcYUof1TBHUTMa1VKNKcBXSfK3NN8pXb49 100
password: *
TXID: 0xae0675797c2d738dcadb21cec3f1809ff453ac291046a05ac679cbd95b79c856
```

要查看资产 ID ，可输入 `list asset` 命令查看钱包中的所有资产。

当从签名数量为 1 以上的多方签名合约地址中转出资产时，需要多方进行签名，此时会返回一段待签名的 json 字符串。

### sign

从签名数量为 1 以上的多方签名合约中提取资产时，需要多方进行签名。 签名完整后才能广播出去。广播交易的方法请参照 [relay](#relay) 方法。

##### 句法

`sign <jsonObjectToSign>` 

##### 参数

`jsonObjectToSign`：记录多方签名交易的 json 字符串。

### relay

将完成签名的交易信息进行广播。

##### 句法

`relay <jsonObjectToSign>` 

##### 参数

`jsonObjectToSign`：记录签名交易的 json 字符串。

### export block[s]

导出全部区块数据，或者从指定区块高度导出指定数量的区块数据，导出的结果可以用作离线同步。要使用此命令，需先安装 [ImportBlocks](https://github.com/BhpAlpha/bhp-plugins/releases) 插件。

##### 句法

`export block[s] [path=chain.acc]`

`export block[s] <start> [count]`

##### 参数

`[path=chain.acc]`：导出全部区块数据

`<start> [count]`：指定要导出数据的起始区块高度和区块数量

