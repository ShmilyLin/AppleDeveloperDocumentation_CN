# launchUserNotificationUserInfoKey

这个Key表示你的App是因为用户在通知中心中激活了通知而启动的。

> SDK : macOS 10.8+

---

## 声明

```swift
class let launchUserNotificationUserInfoKey: String
```

---
## 说明

`launchUserNotificationUserInfoKey`对应的值是一个[NSUserNotification]()对象，如果你的App是因为用户在通知中心中激活了通知而启动了App，则会出现在[didFinishLaunchingNotification]()通知的[userInfo]()字典中。 要访问[userInfo]()字典中的通知有效内容，你可以使用以下代码：

```objectivec
NSUserNotification *userNotification = [[myNotification userInfo]
    objectForKey:NSApplicationLaunchUserNotificationKey];
    if (userNotification) {
        // The app was launched by a user selection from Notification Center.
    }
```

---
## 其他内容

### Keys

#### ● [class let launchIsDefaultUserInfoKey: String](./launchIsDefaultUserInfoKey.md)

此Key的值是一个`Boolean`值转换的`NSNumber`。如果App已启动用于打开或打印文件、执行服务（Service）操作、App已保存将要还原的状态、或者App启动是在其他形式的启动而非默认启动时，则值为`false`。否则它的值将是`true`。