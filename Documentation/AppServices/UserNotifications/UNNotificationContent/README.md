# UNNotificationContent

通知的不可编辑的内容。

## 声明

```swift
class UNNotificationContent : NSObject
```

## 概述

`UNNotificationContent`对象包含与通知关联的数据。当你的应用程序收到通知时，关联的[UNNotificationRequest](../UNNotificationRequest/)对象将包含此类型的对象以及你的应用程序收到的内容。使用`content`对象获取通知的详细信息，包括传递的通知的类型，在计划通知之前存储在[userInfo](#)词典中的所有自定义数据以及任何附件。

不要直接创建此类的实例。对于远程通知，此对象的内容源自服务器发送到APNS服务器的JSON有效负载。 对于本地通知，请创建[UNMutableNotificationContent](../UNMutableNotificationContent/)对象，然后配置该对象的内容。

## 主题

