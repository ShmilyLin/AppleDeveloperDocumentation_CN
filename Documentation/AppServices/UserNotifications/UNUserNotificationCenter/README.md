# UNUserNotificationCenter

管理与你的应用程序或应用程序扩展有关的通知相关活动的中央对象。

## 声明

```swift
class UNUserNotificationCenter : NSObject
```

## 概述

使用共享的`UNUserNotificationCenter`对象来管理你的应用程序或应用程序扩展中与通知有关的所有行为。具体来说，使用此对象可以：

* 请求通过alert，声音和图标标记与用户交互的授权。（所有用户交互都需要授权。）请参阅[请求使用通知的权限](../AskingPermissionToUseNotifications.md)。
* 声明你的应用支持的通知类型以及在传递这些通知时用户可能执行的自定义操作（如果有）。请参阅[声明可操作的通知类型](#)。
* 安排从你的应用发送通知。请参阅[从应用程序本地安排通知](#)。
* 处理Apple推送通知服务（APN）传递的远程通知中的有效负载。请参阅[处理通知和与通知有关的操作](#)。
* 管理通知中心中显示的已发送的通知。请参阅[管理已发送的通知]()。
* 处理与你的自定义通知类型相关的用户选择的操作；请参阅[处理通知和与通知相关的操作](#)。
* 获取你的应用的通知相关设置。 请参阅[管理设置和授权](#)。

要处理传入的通知和与通知有关的操作，请创建一个采用[UNUserNotificationCenterDelegate](#)协议的对象，并将其分配给该对象的[delegate](#)属性。在执行任何可能与该delegate交互的任务之前，始终将一个对象分配给`delegate`属性。 在调用 将信息返回给delegate的方法 之后才分配delegate对象是错误的。

你可以从任何应用程序线程中同时使用共享的`UNUserNotificationCenter`对象。对象按请求的启动顺序，顺序处理请求。

## 主题

### 获得通知中心

* [class func current() -> UNUserNotificationCenter](#) 
    返回你的应用或应用扩展程序的共享的`UNUserNotificationCenter`对象。

### 接收通知和处理措施

* [var delegate: UNUserNotificationCenterDelegate?](#) 
    处理传入通知和与通知相关的操作的对象。

* [protocol UNUserNotificationCenterDelegate](#) 
    用于处理传入通知和通知相关操作的界面。

### 管理设置和授权

* [func requestAuthorization(options: UNAuthorizationOptions, completionHandler: (Bool, Error?) -> Void)](./1649527-requestauthorization.md) 
    当本地和远程通知传递到用户的设备时，请求与用户进行交互的授权。

* [func getNotificationSettings(completionHandler: (UNNotificationSettings) -> Void)](#) 
    请求此应用的通知设置。

* [var supportsContentExtensions: Bool](#) 
    一个布尔值，指示当前设备是否支持通知内容扩展。

* [struct UNAuthorizationOptions](#) 
    用于请求授权以与用户进行交互的常量。

### 注册通知类别

* [func setNotificationCategories(Set)](./1649512-setnotificationcategories.md) 
    注册你的应用的通知类型及其支持的自定义操作。

* [func getNotificationCategories(completionHandler: (Set) -> Void)](#) 
    检索应用程序当前注册的通知类别。

### 计划和取消通知请求

* [func add(UNNotificationRequest, withCompletionHandler: ((Error?) -> Void)?)](#) 
    计划本地通知以进行发送。

* [func getPendingNotificationRequests(completionHandler: \(\[UNNotificationRequest\]\) -> Void\)](#) 
    返回所有已计划并等待发送的通知请求的列表。

* [func removePendingNotificationRequests(withIdentifiers: \[String\]\)](#) 
    取消计划指定的通知请求。

* [func removeAllPendingNotificationRequests()](#) 
    取消计划所有待处理的通知请求。

### 管理已发送的通知

* [func getDeliveredNotifications(completionHandler: \(\[UNNotification\]\) -> Void\)](#) 
    返回仍在通知中心显示的应用程序通知列表。

* [func removeDeliveredNotifications(withIdentifiers: \[String\]\)](#) 
    从通知中心删除指定的通知请求。

* [func removeAllDeliveredNotifications()](#) 
    从通知中心删除所有当前应用发送的通知。

### 处理错误

* [struct UNError](#) 
    通知的错误常量。

* [let UNErrorDomain: String](#) 
    通知的错误域。

