# 安装

你可以通过两种方式安装 Bhp-CLI：

- 直接下载 Bhp-CLI 的官方发布程序包进行安装。
- 或者下载 Bhp-CLI 的源代码并发布成可执行文件，如果使用 macOS，则推荐此方式。

下文将具体介绍这两种方式。

## 配置要求

运行 Bhp-CLI 的计算机需具备以下配置，以获得较佳体验：

|          | 最低配置                                             | 推荐配置                                             |
| -------- | ---------------------------------------------------- | ---------------------------------------------------- |
| 操作系统 | Windows 10<br/>Ubuntu 16.04/18.04<br/>CentOS 7.4/7.6 | Windows 10<br/>Ubuntu 16.04/18.04<br/>CentOS 7.4/7.6 |
| CPU      | 双核                                                 | 四核                                                 |
| 内存     | 8G                                                   | 16G                                                  |
| 硬盘     | 50G 固定硬盘                                         | 100G 固定硬盘                                        |

## 安装 Bhp-CLI 程序包

1. 在 GitHub 上下载系统对应的 [Bhp-CLI](https://github.com/BhpAlpha/bhp-cli/releases) 程序包并解压。

2. 对于 Linux 系统，需要安装 LevelDB 和 SQLite3 开发包。例如，在 ubuntu 18.04 上输入以下命令：

   ```
   sudo apt-get install libleveldb-dev sqlite3 libsqlite3-dev libunwind8-dev
   ```

   对于 Windows 系统，[Bhp-CLI](https://github.com/BhpAlpha/bhp-cli/releases) 的安装包中已经包含了 LevelDB，可跳过该步骤。  

## 阅读下节

[配置与启动 Bhp-CLI](config.md)

