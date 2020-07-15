# 向APN注册你的应用

与APN进行通信，并接收标识你的应用程序的唯一设备令牌。

## 概述

Apple Push Notification Service（APN）必须先知道用户设备的地址，然后才能将通知发送到该设备。该地址采用设备 + 你的应用生成唯一的设备令牌的形式。在启动时，你的应用与APN进行通信并接收其设备令牌，然后将其转发到提供商服务器。你的服务器在发送的所有通知中都包含该令牌。

> **注意**
>
> 一个应用程序的设备令牌不能用于另一个应用程序，即使两个应用程序都安装在同一设备上。这两个应用程序都必须请求自己的唯一设备令牌，并将其转发到你的提供商服务器。

### 启用推送通知功能

应用必须具有适当的权利才能使用推送通知。要将这些权利添加到你的应用程序，请在Xcode项目中启用“推送通知”功能，如图1所示。在iOS中启用此选项会将[APS环境权限](#)添加到该应用程序。在macOS中，它添加了[APS环境（macOS）权限](#)。有关更多信息，请参见Xcode帮助中的[启用推送通知](#)。

> **重要**
>
> 在你的开发人员帐户中，还必须为分配给你的项目的App ID启用推送通知服务。有关配置你的开发者帐户的更多信息，请转到“开发者帐户”页面。

### 注册你的应用并获取应用的设备令牌

在APN中注册你的应用，并获得一个全球唯一的设备令牌，该令牌实际上是你的应用在当前设备上的地址。你的提供商服务器必须具有此令牌，才能将通知传递到设备。

你每次使用Apple提供的API启动应用程序时，便会注册你的应用程序并接收设备令牌。跨平台的注册过程相似：

* 在iOS和tvOS中，调用`UIApplication`的[registerForRemoteNotifications()]()方法以请求设备令牌。成功注册后，你会在应用程序delegate的[application(_:didRegisterForRemoteNotificationsWithDeviceToken:)]()方法中收到令牌。
* 在macOS中，调用`NSApplication`的[registerForRemoteNotifications()]()方法来请求设备令牌。成功注册后，你会在应用程序delegate的[application(_:didRegisterForRemoteNotificationsWithDeviceToken:)]()方法中收到令牌。
* 在watchOS中，你无需明确注册远程通知。用户的iPhone在适当的时间自动将远程通知转发到watchOS应用。

除了通过APN处理成功的注册外，还应准备通过实现[application(_:didFailToRegisterForRemoteNotificationsWithError:)](#)方法来处理不成功的注册。如果用户的设备未连接到网络，APNs服务器由于任何原因无法访问或应用程序没有适当的代码签名权利，则注册可能会失败。发生故障时，请设置一个标志，并在以后尝试再次注册。

下面代码显示了注册远程通知并接收相应令牌所需的iOS应用委托方法的示例实现。`sendDeviceTokenToServer`方法是应用程序用来将数据发送到其提供程序服务器的自定义方法。

```swift
func application(_ application: UIApplication,
           didFinishLaunchingWithOptions launchOptions:
           [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
   // Override point for customization after application launch.
               
   UIApplication.shared.registerForRemoteNotifications()
   return true
}

func application(_ application: UIApplication,
            didRegisterForRemoteNotificationsWithDeviceToken 
                deviceToken: Data) {
   self.sendDeviceTokenToServer(data: deviceToken)
}

func application(_ application: UIApplication,
            didFailToRegisterForRemoteNotificationsWithError 
                error: Error) {
   // Try again later.
}
```

> **重要**
>
> 切勿在本地存储中缓存设备令牌。当用户从备份中还原设备，用户在新设备上安装你的应用程序以及用户重新安装操作系统时，APN会发出新令牌。 如果你要求系统每次提供令牌，则可以保证获得最新的令牌。

### 将令牌转发到你的提供商服务器

收到设备令牌后，打开从你的应用程序到提供商服务器的网络连接。将设备令牌和识别特定用户所需的任何其他信息安全地转发到服务器。例如，你可以包括用户的登录名或将用户连接到你的服务的名称。加密你通过网络发送的所有信息。

在提供商服务器上，将令牌存储在安全的位置，你可以在其中访问令牌以发送通知。生成通知时，你的服务器必须能够将通知发送到特定设备。 因此，如果通知链接到用户的帐户，则将设备令牌与用户的帐户信息一起存储。 因为用户可以拥有多个设备，所以准备处理多个设备令牌。

有关如何将有效负载和设备令牌发送到APN的信息，请参阅[将通知请求发送到APN](#)。