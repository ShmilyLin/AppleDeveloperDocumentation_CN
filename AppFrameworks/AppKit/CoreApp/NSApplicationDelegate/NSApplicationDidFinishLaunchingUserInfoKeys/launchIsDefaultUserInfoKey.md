# launchIsDefaultUserInfoKey

此Key的值是一个`Boolean`值转换的`NSNumber`。如果App已启动用于打开或打印文件、执行服务（Service）操作、App已保存将要还原的状态、或者App启动是在其他形式的启动而非默认启动时，则值为`false`。否则它的值将是`true`。

> SDK : macOS 10.7+

---
## 声明

```swift
class let launchIsDefaultUserInfoKey: String
```

---
## 其他内容

### Keys

#### ● [class let launchUserNotificationUserInfoKey: String](./launchUserNotificationUserInfoKey.md)

这个Key表示你的App是因为用户在通知中心中激活了通知而启动的。