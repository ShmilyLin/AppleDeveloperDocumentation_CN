# applicationDidResignActive(_:)

在App变为不活动状态后，由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationDidResignActive(_ notification: Notification)
```

---

## 参数

* **aNotification**

  名为[didResignActiveNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。

---
## 其他内容

### 管理活动状态

#### ● [func applicationWillBecomeActive(Notification)](./applicationWillBecomeActive.md)

在App变为活动状态之前由默认通知中心（default notification center）发送。

#### ● [func applicationDidBecomeActive(Notification)](./applicationDidBecomeActive.md)

在App变为活动状态后立即由默认通知中心（default notification center）发送。

#### ● [func applicationWillResignActive(Notification)](./applicationWillResignActive.md)

在App变为不活动状态之前，由默认通知中心（default notification center）发送。