# 准备工作

本文将以在 BHP 区块链上发布一个 BRC-20 资产为例，一步步带领开发者完成开发环境的搭建和配置，编写智能合约以及在私链上部署和调用合约。

BHP 有两个全节点客户端：BHP-GUI 和 BHP-CLI。本教程将使用 BHP-CLI 搭建私链供节点连接，使用 BHP-GUI 发布智能合约。

## 系统环境

BHP-GUI 支持以下环境：

Windows 10

BHP-CLI 支持以下环境：

- Linux (ubuntu 16.04 及以上)
- Windows 10

> [!NOTE]
>
> 由于同时涉及到 BHP-GUI 和 BHP-CLI ，建议直接使用 Windows 10 的系统。

## 下载客户端

- BHP-GUI

  进入 [GitHub](https://github.com/BhpAlpha/bhp-gui/releases) 下载最新的Release版本，直接运行 bhp-gui.exe 即可。

- BHP-CLI

  以 Windows 10为例：

  客户端无需安装，进入[GitHub](https://github.com/BhpAlpha/bhp-cli/releases)下载最新的Release版本。