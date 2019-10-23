# applicationDidChangeScreenParameters(_:)

当更改连接到计算机的显示配置时（通过编程方式或用户更改“显示”控制面板中的设置），由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationDidChangeScreenParameters(_ notification: Notification)
```

---
## 参数

* **aNotification**

  名为[didChangeScreenParametersNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。

  