# UserNotificationsUI

自定义显示本地和远程通知的界面。

## 概述

通过将通知内容应用程序扩展添加到iOS应用程序包中，以自定义本地和远程通知在用户设备上的显示方式。你的扩展程序管理一个自定义视图控制器，你可以使用它来显示传入通知中的内容。通知到达时，系统将在默认系统界面之外或代替默认系统界面显示你的视图控制器。

## 主题

### 通知内容应用扩展

* [自定义通知的外观](./CustomizingTheAppearanceOfNotifications.md) 
    使用通知内容应用扩展程序自定义iOS应用的通知alert的外观。

* [protocol UNNotificationContentExtension](./UNNotificationContentExtension/) 
    呈现用于传递的本地或远程通知的自定义界面的对象。