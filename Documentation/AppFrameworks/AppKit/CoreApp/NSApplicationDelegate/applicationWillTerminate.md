# applicationWillTerminate(_:)

在App终止之前由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationWillTerminate(_ notification: Notification)
```

---

## 参数

* **aNotification**

  名为[willTerminateNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。

---
## 说明

你的delegate可以使用此方法在应用程序终止之前执行任何最终清理。

---
## 其他内容

### 终止App

#### ● [func applicationShouldTerminate(NSApplication) -> NSApplication.TerminateReply](./applicationShouldTerminate.md)

发送通知给delegate表示该App即将终止。

#### ● [func applicationShouldTerminateAfterLastWindowClosed(NSApplication) -> Bool](./applicationShouldTerminateAfterLastWindowClosed.md)

当用户关闭App打开的最后一个窗口时调用。

#### ● [enum NSApplication.TerminateReply](./NSApplicationTerminateReply/)

delegate方法[applicationShouldTerminate(_:)](./applicationShouldTerminate.md)使用的常量，来确定应用程序是否应终止。

### 相关文档

#### ● [func terminate(Any?)]()

终止接收器。