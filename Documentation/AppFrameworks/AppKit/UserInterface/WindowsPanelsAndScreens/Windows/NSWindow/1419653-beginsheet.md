# beginSheet(_:completionHandler:)

开始文档模式的会话并呈现（或呈现队列）`Sheet`。

## 定义

```swift
func beginSheet(_ sheetWindow: NSWindow, 
    completionHandler handler: ((NSApplication.ModalResponse) -> Void)? = nil)
```

## 参数

* **sheetWindow**

    代表要显示为`Sheet`的`窗口`对象。

* **handler**

    `Sheet`的模态会话结束时调用的完成处理程序。

## 说明

如果`窗口`已经有一个显示中的`Sheet`，则此方法将指定的`Sheet`排队等待，在取消当前`Sheet`后再将其显示，然后将控制权返回给调用方。

如果`窗口`中没有显示中的`Sheet`，则此方法显示指定的`Sheet`，使其成为`Key`，然后将控制权返回给调用方。当页面仍然可见时，大多数针对接收者的事件都被禁止。Runloop不会进入任何特殊模式来完成此操作。