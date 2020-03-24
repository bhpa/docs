# BHP-CLI SeedList

## 介绍
### 关于 SeedList
简单来说，SeedList 是一个 URL 列表，是 BHP-CLI 在启动时尝试连接的节点。在 bhp-cli 目录下的 `protcol.json` 文件中可以找到 SeedList。

```json
{
  "ProtocolConfiguration": {    
    "Magic": ...,
    "AddressVersion": ...,
    "SecondsPerBlock": ...,
    "LowPriorityThreshold": ...,
    "StandbyValidators": [
      ...
    ],
    "SeedList": [
      "seed01.bhpa.io:20555",
      "seed02.bhpa.io:20555",
      "seed03.bhpa.io:20555",
      "seed04.bhpa.io:20555",
      "seed05.bhpa.io:20555",
      "seed06.bhpa.io:20555",
      "seed07.bhpa.io:20555",
      "seed08.bhpa.io:20555"
    ],
    "SystemFee": {
      ...
    }
  }
}
```
在上面的文件中，BHP-CLI 配置为通过 `PORT:20555` 连接 `seed01.bhpa.io` ，`seed01.bhpa.io` 等系列节点。

### 潜在的问题
假如以上列表中的每个节点故障，BHP-CLI 会尝试连接相邻节点。但是这种方法存在很多未知因素，例如相邻节点出问题了，可能导致等待时间相当漫长。

## 阅读下节

[命令参考](cli.md)

