# endSheet(_:returnCode:)

结束文档模式会话并关闭指定的`Sheet`。

## 定义

```swift
func endSheet(_ sheetWindow: NSWindow, 
                 returnCode: NSApplication.ModalResponse)
```

## 参数

* **sheetWindow**

    代表要被关闭的`Sheeet`对应的`窗口`对象。

* **returnCode**

    返回代码，发送给完成处理程序。你可以使用定义的自定义值，也可以使用[NSApplication.ModalResponse]()枚举或其他`NSModalResponse`值中定义的返回码之一。

## 说明

此方法以指定的返回码结束模式会话。