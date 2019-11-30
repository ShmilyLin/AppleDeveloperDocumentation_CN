# applicationWillUpdate(_:)

在App对象更新其窗口之前，由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationWillUpdate(_ notification: Notification)
```

---
## 参数

* **aNotification**

  名为[willUpdateNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。


---
## 其他内容

### 管理窗口

#### ● [func applicationDidUpdate(Notification)](./applicationDidUpdate.md)

在App对象更新其窗口之后，由默认通知中心（default notification center）发送。

#### ● [func applicationShouldHandleReopen(NSApplication, hasVisibleWindows: Bool) -> Bool](./applicationShouldHandleReopenHasVisibleWindows.md)

在默认行为之前由App发送给delegate以重新打开（rapp）AppleEvents。

### 相关文档

#### ● [func updateWindows()]()

向每个屏幕窗口发送[update()]()消息。