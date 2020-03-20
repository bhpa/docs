# 钱包

钱包是 BHP 的基础组件，是用户接入 BHP 网络的载体，负责完成与之相关一系列的工作和任务。

BHP 的钱包可以自行设计和修改，但需要满足一定的规则。

##  格式

### 私钥

私钥是一个随机生成的位于1和n之间的任何数字（n是⼀个常数，略小于2的256次方），一般用一个256bit(32字节)数表示。

在 BHP 中私钥主要采用两种编码格式：

- hexstring 格式

   hexstring 格式是将byte[]数据使用16进制字符表示的字符串。

- wif 格式

   wif 格式是在原有 32 字节数据前后添加前缀 0x80 和后缀 0x01 ,并做 Base58Check 编码的字符串

 Example: 

| 格式 | 数值 |
|---|---|
| byte[] | [0x53,0x116,0x178,0x44,0x79,0x170,0x236,0x228,0x28,0x172,0x215,0x190,0x255,0x91,0x21,0x137,0x214,0x219,0x209,0x178,0x81,0x207,0x158,0x210,0x10,0x189,0x194,0x248,0x31,0x109,0x62,0x01] |
| hexstring | 3574b22c4faaece41cacd7beff5b1589d6dbd1b251cf9ed20abdc2f81f6d3e01 |
| wif | 6PYTDmusDiSixF9jynpJoFeCtexdy1L2Qfx2Y3umaSatdHHxzRnhgUv3dT |

### 公钥

公钥是通过ECC算法将私钥运算得到的一个点（X, Y）。该点的X、Y坐标都可以用32字节数据表示。在BHP 中公钥有两种编码格式：

- 非压缩型公钥

    0x04 + X坐标（32字节）+ Y坐标（32字节）

- 压缩型公钥

    0x02 + X坐标（32字节）或者 0x03 + X坐标（32字节）

Example:

| 格式 | 数值 |
|----------|:-------------:|
| 私钥 | 3574b22c4faaece41cacd7beff5b1589d6dbd1b251cf9ed20abdc2f81f6d3e01 |
| 公钥（压缩型） | 020a2a4f2ef618d7d38606c2a65ff941b8898d00cdade6e4ed2437052cffde16d2 |
| 公钥（非压缩型） | 040a2a4f2ef618d7d38606c2a65ff941b8898d00cdade6e4ed2437052cffde16d23e9627550b107bac5f3e26fc766a93ea496b17be5023a97eee0ba3769f379dae |

### 地址

地址是由公钥经过一系列转换得到的一串由数字和字母构成的字符串。在 BHP 中，公钥到地址的转换步骤如下：

1. 构建地址脚本合约，脚本合约格式：

    `0x21`(1字节,代表`OptCode.PUSHBYTES21`指令) + 压缩型公钥(33字节) + `0xac`（1字节,代表`OptCode.CHECKSIG`指令)

2. 计算地址脚本合约哈希 (20字节，由地址脚本合约先做一次 SHA256 再做一次 RIPEMD160 得到)

3. 在地址脚本合约哈希前添加版本号（目前 BHP 所使用的协议版本是 23 所以对应字节为`0x17`）

4. 对字节数据做 Base58Check 编码

示例：

| 格式 | 数值 |
|----------|:-------------:|
| 私钥 | 3574b22c4faaece41cacd7beff5b1589d6dbd1b251cf9ed20abdc2f81f6d3e01 |
| 压缩型公钥 | 020a2a4f2ef618d7d38606c2a65ff941b8898d00cdade6e4ed2437052cffde16d2 |
| 地址 | AXfgAN3coFD1LXbAyCnnMS8LmmSNVrJCt9 |

### 数字证书

数字证书是一个经证书授权中心数字签名的包含公开密钥拥有者信息以及公开密钥的文件。BHP 使用X509格式的证书。

## 钱包文件

### db3 钱包文件

db3 钱包文件是 BHP 采用 sqlite 技术存储数据所使用存储文件，文件尾缀名：`.db3`。 文件中主要存储以下四个属性：

- `PasswordHash`：密码的哈希，由密码做 sha256 得到

- `IV`：AES的初始向量，随机生成

- `MasterKey`：加密密文，由 PasswordHash、 IV 对私钥做 AES256 加密得到

- `Version`：版本

db3 钱包采用对称加密 AES 相关技术作为钱包的加密和解密方法。

### BRC6 钱包文件

BRC6 钱包文件是 BHP 满足 BRC6 标准的钱包存储数据所使用存储文件，文件尾缀名：`.json`。 json文件格式如下：

```json
{
	"name": null,
	"version": "1.0",
	"scrypt": {
		"n": 16384,
		"r": 8,
		"p": 8
	},
	"accounts": [
		{
			"address": "AXfgAN3coFD1LXbAyCnnMS8LmmSNVrJCt9",
			"label": null,
			"isDefault": false,
			"lock": false,
			"key": "6PYTDmusDiSixF9jynpJoFeCtexdy1L2Qfx2Y3umaSatdHHxzRnhgUv3dT",
			"contract": {
				"script": "21020a2a4f2ef618d7d38606c2a65ff941b8898d00cdade6e4ed2437052cffde16d2ac",
				"parameters": [
					{
						"name": "signature",
						"type": "Signature"
					}
				],
				"deployed": false
			},
			"extra": null
		}		
	],
	"extra": null
}
```

**属性说明**：

- `name`：用户给该钱包添加的名称

- `version`：钱包版本，目前固定为 1.0，在以后功能升级时可能会改变

- `scrypt`（n/r/p）：scrypt 算法设置计算性能的三个参数

- `accounts`：钱包所包含的账户的集合

- `address`:账户地址

- `label`：标题

- `isDefault`：是否默认账户

- `lock`：是否打开

- `key`：按照 BRC2 标准加密的密钥 brc2Key

- `contract`：地址脚本合约的详细内容

- `script`：地址脚本合约的字节

- `parameters`：地址脚本合约的参数表

- `parameters.name`：地址脚本合约参数的名称

- `type`：地址脚本合约参数的类型

- `deployed`：是否部署

- `accounts.extra`：账户其他扩展属性

- `extra`：钱包其他扩展属性

BRC 6钱包采用了以 scrypt 为核心算法的相关技术作为钱包的加密和解密方法。

**加密过程**：

1. 由公钥计算地址，并获取`SHA256(SHA256(Address))`的前四个字节作为地址哈希

2. 使用 Scrypt 算法算出一个`derivedkey`，并将其 64 个字节数据分成 2 半，作为`derivedhalf1`和`derivedhalf2`。Scrypt 所使用参数如下：

	- 明文：输入的密码（UTF-8格式）
	- 盐：地址哈希
	- n：16384
	- r：8
	- p：8
	- length：64

3. 把私钥和 derivedhalf1 做异或，然后用 derivedhalf2 对其做 AES256 加密得到 encryptedkey

4. 按照以下格式拼接数据，并对其做Base58Check编码得到NEP2Key：

    `0x01` + `0x42` + `0xe0` + `地址哈希` + `encryptedkey`

**解密过程**：

1. 对 BRC2key 做 Base58Check 解码

2. 验证解码后数据长度为 39，以及前 3 个字节（data[0-2]是否为0x01、0x42、0xe0）

3. 取data[3-6]作为`addresshash`

4. 把密码、addresshash 代入 Scrypt 算法，指定结果长度为 64，求出`derivedkey`

5. 把`derivedkey`前32字节作为`derivedhalf1`，后32字节作为`derivedhalf2`

6. 取data[7-38]作为`encryptedkey`（32字节），并用 derivedhalf2 作为初始向量对其进行 AES256 解密

7. 把解密结果与 Derivedhalf1 做异或处理求得私钥

8. 把该私钥做 ECC 求出公钥，并生成地址，对该地址做 2 次 Sha256 然后取结果的前四字节判断其是否与 addresshash 相同，相同则是正确的私钥

## 钱包功能

| 功能名称       | 描述                                                       |
| -------------- | ---------------------------------------------------------- |
| 导入钱包文件   | 从指定钱包文件导入账户信息                                 |
| 导出钱包文件   | 将账户信息导出到指定的钱包文件，如 db3 文件、BRC6 json文件 |
| 解锁钱包       | 验证用户密码来防止账户信息泄露                             |
| 生成私钥       | 推荐使用安全的随机数发生器                                 |
| 导入私钥       | 从WIF字符串或者数字证书导入私钥到钱包中                    |
| 导出私钥       | 导出账户的私钥                                             |
| 生成公钥       | 使用ECC算法从私钥得到公钥                                  |
| 生成地址       | 从私钥生成地址                                             |
| 导入地址       | 添加新的地址到钱包中                                       |
| 导出地址       | 导出账户地址                                               |
| 导入离线数据包 | 从`chain.acc`文件加载区块数据来减少同步时间                |
| 导出离线数据包 | 导出区块数据到`chain.acc`文件                              |
| 同步区块数据   |                                                            |
| 转账           | 转账资产到其他地址                                         |
| 签名           | 对数据签名，比如交易                                       |
| 提取gas        | 提取通过持有neo新分配的gas                                 |
| 获取余额       | 显示该钱包中所有账户的资产余额                             |
| 获取交易       | 显示该钱包中产生的交易历史                                 |
| 构造多签合约   | 构造多签合约                                               |
| 扩展           |                                                            |
| 部署智能合约   | 部署智能合约                                               |
| 测试智能合约   | 测试智能合约                                               |

## 钱包软件

### 全节点钱包

全节点钱包包含所有区块数据的备份，保存了所有链上数据，并且参与p2p网络通信，所以占用存储空间较大。

BHP-CLI 和 BHP-GUI 都是全节点钱包。

### SPV钱包

SPV (Simplified Payment Verification, 简单支付验证)钱包不同于全节点钱包，它不会存储所有的区块数据，仅存储区块头数据，并使用布隆过滤器和梅克尔树算法。它主要在移动端 App 或者轻节点中使用，因为它能有效得节省存储空间。

如果要开发 SPV 钱包，请参考 BHP 网络协议接口。

使用：

    1. SPV钱包发送一个布隆过滤器到全节点，全节点加载该布隆过滤器。
    
    2. SPV钱包发送布隆过滤器的参数到全节点，全节点加载该布隆过滤器的参数。（可选）
    
    3. SPV钱包从全节点查询交易，全节点在使用布隆过滤器过滤后返回交易数据和构造的梅克尔树路径。
    
    4. SPV钱包使用梅尔克树路径来验证交易数据。
    
    5. SPV钱包发送`clear the bloom filter`指令给全节点，全节点清楚该布隆过滤器。

