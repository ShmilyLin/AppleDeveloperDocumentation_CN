# applicationDidHide(_:)

在隐藏App之后，由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationDidHide(_ notification: Notification)
```

---

## 参数

* **aNotification**

  名为[didHideNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。


---
## 其他内容

### 隐藏App

#### ● [func applicationWillHide(Notification)](./applicationWillHide.md)

在隐藏App之前，由默认通知中心（default notification center）发送。

#### ● [func applicationWillUnhide(Notification)](./applicationWillUnhide.md)

在取消隐藏App之前，由默认通知中心（default notification center）发送。

#### ● [func applicationDidUnhide(Notification)](./applicationDidUnhide.md)

在取消隐藏App之后，由默认通知中心（default notification center）发送。

### 相关文档

#### ● [func unhide(Any?)]()

将隐藏的窗口恢复到屏幕并使接收器处于活动状态。