# NSApplication.TerminateReply

delegate方法[applicationShouldTerminate(_:)](./applicationShouldTerminate.md)使用的常量，来确定应用程序是否应终止。

> SDK : macOS 10.0+

---
## 专题

### 常量

#### ● [case terminateNow](./terminateNow.md)

可以继续终止。

#### ● [case terminateCancel](./terminateCancel.md)

该应用程序不应被终止。

#### ● [case terminateLater](./terminateLater.md)

---
## 其他内容

### 终止App

#### ● [func applicationShouldTerminate(NSApplication) -> NSApplication.TerminateReply](../applicationShouldTerminate.md)

发送通知给delegate表示该App即将终止。

#### ● [func applicationShouldTerminateAfterLastWindowClosed(NSApplication) -> Bool](../applicationShouldTerminateAfterLastWindowClosed.md)

当用户关闭App打开的最后一个窗口时调用。

#### ● [func applicationWillTerminate(Notification)](../applicationWillTerminate.md)

在App终止之前由默认通知中心（default notification center）发送。