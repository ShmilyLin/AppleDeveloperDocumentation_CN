# NSApplicationDidFinishLaunching User Info Keys

这之下的常量定义了[didFinishLaunchingNotification]()中可以存在的key。

---
## 专题

### Keys

#### ● [class let launchIsDefaultUserInfoKey: String](./launchIsDefaultUserInfoKey.md)

此Key的值是一个`Boolean`值转换的`NSNumber`。如果App已启动用于打开或打印文件、执行服务（Service）操作、App已保存将要还原的状态、或者App启动是在其他形式的启动而非默认启动时，则值为`false`。否则它的值将是`true`。

#### ● [class let launchUserNotificationUserInfoKey: String](./launchUserNotificationUserInfoKey.md)

这个Key表示你的App是因为用户在通知中心中激活了通知而启动的。

--- 
## 其他内容

### 启动App

#### ● [func applicationWillFinishLaunching(Notification)](../applicationWillFinishLaunching.md)

在App对象初始化之前由默认通知中心（default notification center）发送。

#### ● [func applicationDidFinishLaunching(Notification)](../applicationDidFinishLaunching.md)

在App启动并初始化之后，但在收到第一个事件之前，由默认通知中心（default notification center）发送。