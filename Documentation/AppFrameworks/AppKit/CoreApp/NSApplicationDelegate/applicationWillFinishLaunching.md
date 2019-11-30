# applicationWillFinishLaunching(_:)

在App对象初始化之前由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationWillFinishLaunching(_ notification: Notification)
```

---
## 参数

* **aNotification**

  名为[willFinishLaunchingNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。

---
## 其他内容

### 启动App

#### ● [func applicationDidFinishLaunching(Notification)](./applicationDidFinishLaunching.md)

在App启动并初始化之后，但在收到第一个事件之前，由默认通知中心（default notification center）发送。

#### ● [NSApplicationDidFinishLaunching User Info Keys](./NSApplicationDidFinishLaunchingUserInfoKeys/)

其下的常量定义了[didFinishLaunchingNotification]()中可以存在的key。

### 相关文档

#### ● [func applicationWillBecomeActive(Notification)]()
在App变为活动状态之前由默认通知中心（default notification center）发送。

#### ● [Sheet Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Sheets/Sheets.html#//apple_ref/doc/uid/10000002i)

#### ● [func finishLaunching()]()

激活App，通过[NSOpen]()打开用户默认指定的任何文件，并取消突出显示应用程序的图标。

#### ● [Services Implementation Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/SysServices/introduction.html#//apple_ref/doc/uid/10000101i)
#### ● [Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)
#### ● [Local and Remote Notification Programming Guide](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/index.html#//apple_ref/doc/uid/TP40008194)
#### ● [Notification Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Notifications/Introduction/introNotifications.html#//apple_ref/doc/uid/10000043i)