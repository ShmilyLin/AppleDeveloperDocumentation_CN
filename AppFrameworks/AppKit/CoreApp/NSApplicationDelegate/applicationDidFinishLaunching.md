# applicationDidFinishLaunching(_:)

在App启动并初始化之后，但在收到第一个事件之前，由默认通知中心（default notification center）发送。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationDidFinishLaunching(_ notification: Notification)
```

---

## 参数

* **aNotification**

  名为[didFinishLaunchingNotification]()的通知。调用此通知的[object]()方法将返回[NSApplication](../NSApplication/)对象本身。

---
## 说明

Delegate可以实现此方法以执行进一步的初始化。在App的主运行循环已经启动但尚未开始处理任何事件之前调会用此方法。如果App是由用户打开文件启动的，则在此方法之前调用delegate的[application(_:openFile:)]()方法。如果要在打开任何文件之前执行初始化，请在delegate中实现[applicationWillFinishLaunching(_:)](./applicationWillFinishLaunching.md)方法，该方法在[application(_:openFile:)]()之前调用。

---
## 其他内容

### 启动App

#### ● [func applicationWillFinishLaunching(Notification)](./applicationWillFinishLaunching.md)

在App对象初始化之前由默认通知中心（default notification center）发送。

#### ● [NSApplicationDidFinishLaunching User Info Keys](./NSApplicationDidFinishLaunchingUserInfoKeys/)

其下的常量定义了[didFinishLaunchingNotification]()中可以存在的key。

### 相关文档

#### ● [func finishLaunching()]()

激活App，通过[NSOpen]()打开用户默认指定的任何文件，并取消突出显示应用程序的图标。

#### ● [func application(NSApplication, openFile: String) -> Bool]()

告诉delegate打开一个文件。

#### ● [func applicationDidBecomeActive(Notification)]()

在App变为活动状态后立即由默认通知中心（default notification center）发送。