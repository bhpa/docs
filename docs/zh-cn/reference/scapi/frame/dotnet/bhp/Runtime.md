# Runtime 类

提供智能合约运行时的一些方法。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static class Runtime
```

## 属性

|                                          | 名称                            | 说明                         |
| ---------------------------------------- | ----------------------------- | -------------------------- |
| ![attribute](../../../../../assets/attribute.jpeg) | [Trigger](Runtime/Trigger.md) | 获得该智能合约的触发条件（鉴权合约 or 应用合约） |

## 方法

|                                          | 名称                                       | 说明                            |
| ---------------------------------------- | ---------------------------------------- | ----------------------------- |
| ![function](../../../../../assets/function.jpeg) | [CheckWitness(byte[])](Runtime/CheckWitness.md) | 验证调用该智能合约的交易 / 区块是否验证过所需的脚本散列 |
| ![function](../../../../../assets/function.jpeg) | [Log(string)](Runtime/Log.md)            | 在智能合约中向执行该智能合约的客户端发送日志        |
| ![function](../../../../../assets/function.jpeg) | [Notify(params object[])](Runtime/Notify.md) | 在智能合约中向执行该智能合约的客户端发送通知        |


# 构造方法

Runtime 类是静态类，无需构造方法。