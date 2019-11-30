# applicationShouldTerminate(_:)

发送通知给delegate表示该App即将终止。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationShouldTerminate(_ sender: NSApplication) -> NSApplication.TerminateReply
```

---
## 参数

* **sender**

  即将终止的App对象。

---
## 返回值

[NSApplication.TerminateReply]()常量中定义的值之一，指示App是否应终止。出于兼容性原因，返回值`false`等效于[NSApplication.TerminateReply.terminateCancel]()，返回值`true`等效于[NSApplication.TerminateReply.terminateNow]()。

---
## 说明

在选择App的“退出”菜单项之后，或者在调用[terminate(_:)]()方法之后调用此方法。通常，你应该返回[NSApplication.TerminateReply.terminateNow]()以允许终止完成，但你可以根据需要取消终止过程或稍微延迟。例如，你可能会延迟终止以完成处理某些关键数据，但随后完成后通过调用[reply(toApplicationShouldTerminate:)]()方法立即终止应用程序。

---
## 其他内容

### 终止App

#### ● [func applicationShouldTerminateAfterLastWindowClosed(NSApplication) -> Bool](./applicationShouldTerminateAfterLastWindowClosed.md)

当用户关闭App打开的最后一个窗口时调用。

#### ● [func applicationWillTerminate(Notification)](./applicationWillTerminate.md)

在App终止之前由默认通知中心（default notification center）发送。

#### ● [enum NSApplication.TerminateReply](./NSApplicationTerminateReply/)

delegate方法[applicationShouldTerminate(_:)](./applicationShouldTerminate.md)使用的常量，来确定应用程序是否应终止。

### 相关文档

#### ● [func terminate(Any?)]()

终止接收器。

