# Runtime.Trigger 属性

获得该智能合约的触发器类型（鉴权合约 or 应用合约）。

命名空间：[Bhp.SmartContract.Framework.Services.Bhp](../../bhp.md)

程序集：Bhp.SmartContract.Framework

## 语法

```c#
public static extern Bhp.SmartContract.Framework.Services.Bhp.TriggerType Trigger { get; }
```

属性值：[TriggerType](../TriggerType.md)。

## 示例

```c#
public static bool Main()
{
    if (Runtime.Trigger == TriggerType.Verification)
    {
        // do something;
    }
    else if (Runtime.Trigger == TriggerType.Application)
    {
        // do something;
    }
}
```



[返回上级](../Runtime.md)