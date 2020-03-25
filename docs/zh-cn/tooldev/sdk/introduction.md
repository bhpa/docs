# 关于BHP SDK

可使用 BHP SDK 来开发各种基于 BHP 的应用，如钱包客户端，游戏等。 引用 BHP SDK 后，您的项目仍可在原有的环境中运行，而非在BhpVM中运行，如果想开发在 BhpVM中运行的程序，请参考 [BHP 智能合约](../../smartcontract/start/introduction.md)。

## 项目构成

完整的 BHP SDK 主要由两个项目以及众多依赖项构成：

**BHP SDK主要项目：**

BHP：https://github.com/BhpAlpha/bhp-cli

BhpVM：https://github.com/BhpAlpha/bhp-vm

**BHP SDK依赖项：**

.NETFramework 4.7

- Akka (>= 1.3.8)

- Microsoft.AspNetCore.Server.Kestrel (>= 2.1.1)

- Microsoft.AspNetCore.Server.Kestrel.Https (>= 2.1.1)

- Microsoft.AspNetCore.ResponseCompression (>= 2.1.1)

- Microsoft.AspNetCore.WebSockets (>= 2.1.1)

- Microsoft.EntityFrameworkCore.Sqlite (>= 2.1.1)

- Microsoft.Extensions.Configuration.Json (>= 2.1.1)

- System.Text.Encodings.Web (>= 4.5.0)

- Replicon.Cryptography.SCrypt (>= 1.1.6.13)

.NETStandard 2.0

- Akka (>= 1.3.8)

- Microsoft.AspNetCore.ResponseCompression (>= 2.1.1)

- Microsoft.AspNetCore.Server.Kestrel (>= 2.1.1)

- Microsoft.AspNetCore.Server.Kestrel.Https (>= 2.1.1)

- Microsoft.AspNetCore.WebSockets (>= 2.1.1)

- Microsoft.EntityFrameworkCore.Sqlite (>= 2.1.1)

- Microsoft.Extensions.Configuration.Json (>= 2.1.1)

- System.Text.Encodings.Web (>= 4.5.0)
