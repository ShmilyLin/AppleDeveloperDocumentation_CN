# UserNotifications

将面向用户的通知从服务器推送到用户的设备，或从你的应用本地生成。



## 概述

面向用户的通知将重要信息传达给你的应用程序的用户，无论你的应用程序是否在用户设备上运行。例如，体育应用可以让用户知道他们最喜欢的球队何时得分。通知还可以告诉你的应用下载信息并更新其界面。通知可以显示警报，播放声音或标记应用程序的图标。

你可以从你的应用本地生成通知，也可以从你管理的服务器远程生成通知。对于本地通知，该应用创建通知内容并指定触发通知传递的条件，例如时间或位置。对于远程通知（也称为推送通知），你使用公司的服务器之一来生成通知，而Apple推送通知服务（APN）负责将这些通知传递到用户的设备。

使用此框架可以：

* 定义你的应用支持的通知类型。
* 定义与你的通知类型关联的所有自定义操作。
* 安排要发送的本地通知。
* 处理已经传递的通知。
* 响应用户选择的操作。

> 注意：
>
> 尽一切努力及时传递本地和远程通知，但不能保证传递。 PushKit框架为特定类型的通知（例如用于VoIP和watchOS复杂情况的通知）提供了更及时的传递机制。 有关更多信息，请参见[PushKit](#)。

## 主题

### 要点

* [请求使用通知的权限](./AskingPermissionToUseNotifications.md)
    要求获得显示警报，播放声音或标记应用图标的权限，以响应通知。

### 通知管理

* [class UNUserNotificationCenter](#)
    管理与你的应用程序或应用程序扩展有关的通知相关活动的中央对象。

* [protocol UNUserNotificationCenterDelegate](#)
    用于处理传入通知和通知相关操作的界面。

* [class UNNotificationSettings](#)
    用于管理与通知相关的设置和应用程序的授权状态的对象。

### 远程通知

从你公司的服务器生成通知，并使用APN传递这些通知。

* [设置远程通知服务器](#) 
    设置服务器以生成通知并将其推送到用户设备。

* [向APN注册你的应用](./RegisteringYourAppWithAPNs.md) 
    与APN进行通信，并接收标识你的应用程序的唯一设备令牌。

### 通知请求

创建本地通知的发送请求，并访问发送的本地和远程通知的内容。

* [通过应用本地计划通知]()
    当你想引起用户的注意时，可以从你的应用程序创建和计划通知。

* [class UNNotificationRequest](#) 
    计划本地通知的请求，其中包括通知的内容和发送的触发条件。

* [class UNNotification](#) 
    传递到你的应用程序的本地或远程通知的数据。

### 通知内容

修改并检查通知的有效负载。

* [UNMutableNotificationContent](#) 
    通知的可编辑内容。

* [class UNNotificationContent](#) 
    通知的不可编辑的内容。

* [class UNNotificationAttachment](#) 
    与通知关联的媒体文件。

* [class UNNotificationSound](#) 
    发出通知时播放的声音。

* [struct UNNotificationSoundName](#) 
    提供声音文件名称的字符串。

### 触发



### 通知类别和用户操作

定义你的应用支持的通知类型，并定义用户如何响应。

* [声明你允许使用的通知类型](./DeclaringYourActionableNotificationTypes.md) 
    区分你的通知，并将操作按钮添加到通知界面。

* [class UNNotificationCategory](./UNNotificationCategory/) 
    你的应用支持的一种通知类型，以及与之一起显示的自定义操作。

* [class UNNotificationAction](#) 
    执行一个已发送的通知的任务响应。

* [class UNTextInputNotificationAction](#) 
    可以接受用户键入的文本的操作。

### 通知响应



### 通知服务应用程序扩展

使用通知服务应用程序扩展，在将通知内容传递到你的应用程序之前对其进行修改。

* [修改新发送的通知中的内容](#) 
    在将远程通知的有效负载显示在用户的iOS设备上之前，对其进行修改。

* [class UNNotificationServiceExtension](#) 
    在将远程通知的内容传递给用户之前修改其内容的对象。

### 权限

* [APS环境权限](#) 
    推送通知的环境。
    **key**: aps-environment
* [APS环境（macOS）权限](#)
    macOS应用中用于推送通知的环境。
    **Key:** com.apple.developer.aps-environment