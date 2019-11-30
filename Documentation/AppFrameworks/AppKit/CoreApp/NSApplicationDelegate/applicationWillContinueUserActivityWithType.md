# application(_:willContinueUserActivityWithType:)

告诉delegate用户想要在你的应用中继续活动。

> SDK : macOS 10.+

---

## 声明

```swift
          optional func application(_ application: NSApplication, 
willContinueUserActivityWithType userActivityType: String) -> Bool
```

---
## 参数

* **application**

  保持用户活动的App。

* **userActivityType**

  要保持的活动类型。

---
## 返回值

如果你通知用户你的App将继续活动，则为`true`，如果你希望AppKit通知用户，则为`false`。

---
## 说明

使用此方法可以立即向用户反馈活动即将在此设备上继续运行。一旦用户确认应该继续活动应用程序就会调用此方法，但调用时机可能在与该活动相关联的数据可用之前。

一旦用户表明他们想要在你的应用中继续活动，就会在主线程上调用此方法。[NSUserActivity]()对象可能无法立即使用，因此请将此用作向用户显示活动将很快继续并返回`true`的机会。如果将此方法未实现或返回`false`，则AppKit将显示默认指示。

对于此方法的每次调用，App的delegate将保证在成功时只调用一次`application(_:continue:restorationHandler:)`，如果遇到错误，则调用`application(_:didFailToContinueUserActivityWithType:error:)`。
