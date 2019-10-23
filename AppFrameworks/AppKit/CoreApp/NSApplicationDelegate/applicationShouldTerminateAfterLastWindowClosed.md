# applicationShouldTerminateAfterLastWindowClosed(_:)

当用户关闭App打开的最后一个窗口时调用。

---
## 声明

```swift
optional func applicationShouldTerminateAfterLastWindowClosed(_ sender: NSApplication) -> Bool
```

--- 
## 参数

* **theApplication**

  关闭的最后一个窗口的App对象。

--- 
## 返回值

如果App在其最后一个窗口关闭时不应终止，则为`false`; 否则，`true`表示终止App。

> SDK : macOS 10.0+

---
## 说明

App的最后一个窗口关闭时，App将此消息发送给你的delegate。无论是否仍打开面板，它都会发送此消息。（在这种情况下，面板被定义为[NSPanel]()或其子类之一。）

如果你的实现返回`false`，则控制返回主事件循环，并且App不会终止。如果返回`true`，则随后调用delegate的[applicationShouldTerminate(_:)](./applicationShouldTerminate.md)方法以确认应终止应用程序。

---
## 其他内容

### 终止App

#### ● [func applicationShouldTerminate(NSApplication) -> NSApplication.TerminateReply](./applicationShouldTerminate.md)

发送通知给delegate表示该App即将终止。

#### ● [func applicationWillTerminate(Notification)](./applicationWillTerminate.md)

在App终止之前由默认通知中心（default notification center）发送。

#### ● [enum NSApplication.TerminateReply](./NSApplicationTerminateReply/)

delegate方法[applicationShouldTerminate(_:)](./applicationShouldTerminate.md)使用的常量，来确定应用程序是否应终止。

### 相关文档

#### ● [func terminate(Any?)]()

终止接收器。