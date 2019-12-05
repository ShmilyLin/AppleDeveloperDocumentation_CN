# splitViewDidResizeSubviews(_:)

默认通知中心调用以通知`Delegate`，`分隔视图`已经调整完其`子视图`的大小。

## 定义

```swift
optional func splitViewDidResizeSubviews(_ notification: Notification)
```

## 参数

* **aNotification**

    名为[didResizeSubviewsNotification]()的通知。

## 说明

如果`Delegate`实现此方法，则将自动注册`Delegate`以接收此通知。

`分隔视图`调整其两个`子视图`的大小以响应分隔线的重新定位后将调用此方法。