# endSheet(_:)

结束文档模式会话并关闭指定的`Sheet`。

## 定义

```swift
func endSheet(_ sheetWindow: NSWindow)
```

## 参数

* **sheetWindow**

    代表要被关闭的`Sheeet`对应的`窗口`对象。

## 说明

此方法以返回代码`NSModalResponseStop`结束模态会话。