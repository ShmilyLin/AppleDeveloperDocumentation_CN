# beginCriticalSheet(_:completionHandler:)

启动文档模式会话并显示指定的`Critical Sheet`。

## 定义

```swift
func beginCriticalSheet(_ sheetWindow: NSWindow, 
            completionHandler handler: ((NSApplication.ModalResponse) -> Void)? = nil)
```

## 参数

* **sheetWindow**

    代表要显示为`Sheet`的`窗口`对象。`Critical Sheet`包含对用户来说时间紧迫或非常重要的内容。

* **handler**

    `Sheet`的模态会话结束时调用的完成处理程序。

## 说明

此方法在`窗口`的当前`Sheet`（如果存在）的顶部显示`Sheet`，使其成为`Key`，并将控制权返回给调用者。当页面仍然可见时，大多数针对接收者的事件都被禁止。Runloop不会进入任何特殊模式来完成此操作。

如果运行此方法时`窗口`中已有`Sheet`，则在显示`Critical Sheet`时会暂时禁用现有`Sheet`。销毁`Critical Sheet`后，先前显示的`Sheet`将继续其标准操作。