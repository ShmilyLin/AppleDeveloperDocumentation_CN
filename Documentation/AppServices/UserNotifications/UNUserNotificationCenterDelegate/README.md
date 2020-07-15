# UNUserNotificationCenterDelegate

用于处理传入通知和通知相关操作的界面。

## 定义

```swift
protocol UNUserNotificationCenterDelegate
```

## 概述

使用`UNUserNotificationCenterDelegate`协议的方法来处理通知中用户选择的操作，并处理当应用程序在前台运行时到达的通知。在对象中实现这些方法之后，将该对象分配给共享的[UNUserNotificationCenter](../UNUserNotificationCenter)对象的`delegate`属性。 用户通知中心对象在适当的时间调用delegate的方法。

> **重要**
>
> 你必须在应用启动完成之前将delegate对象分配给[UNUserNotificationCenter](../UNUserNotificationCenter)对象。 例如，在iOS应用程序中，你必须在应用程序委托的[application(_:willFinishLaunchingWithOptions:)](#)或[application(_:didFinishLaunchingWithOptions:)]()方法中进行分配。在调用这些方法之后分配委托可能会导致你错过传入的通知。

有关共享`UNUserNotificationCenter`对象的信息，请参阅[UNUserNotificationCenter](../UNUserNotificationCenter)。

## 主题

### 第一步

* [处理通知和与通知相关的操作](#) 
    响应用户与系统通知界面的交互，包括处理应用程序的自定义操作。

### 处理自定义动作的选择

* [func userNotificationCenter(UNUserNotificationCenter, didReceive: UNNotificationResponse, withCompletionHandler: () -> Void)](#) 
    要求delegate处理用户对传递的通知的响应。

### 接收通知

* [func userNotificationCenter(UNUserNotificationCenter, willPresent: UNNotification, withCompletionHandler: (UNNotificationPresentationOptions) -> Void)](#) 
    询问delegate如何处理在前台运行应用程序时到达的通知。

* [struct UNNotificationPresentationOptions](#) 
    指示如何在前台应用程序中呈现通知的常量。

### 显示通知设置

* [func userNotificationCenter(UNUserNotificationCenter, openSettingsFor: UNNotification?)](#) 询问delegate显示应用内通知设置。

