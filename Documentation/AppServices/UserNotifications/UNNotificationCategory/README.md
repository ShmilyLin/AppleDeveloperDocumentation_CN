# UNNotificationCategory

你的应用支持的一种通知类型，以及与之一起显示的自定义操作。

## 声明

```swift
class UNNotificationCategory : NSObject
```

## 概述

`UNNotificationCategory`对象定义接收的可执行的通知类型。你创建`category`对象来定义应用程序的可操作通知，即具有用户可以选择以响应通知的操作按钮的通知。你创建的每个`category`对象都存储了与特定类型的通知关联的动作和其他行为。使用[UNUserNotificationCenter](../UNUserNotificationCenter/)的[setNotificationCategories(_:)](../UNUserNotificationCenter/1649512-setnotificationcategories.md)方法注册`category`对象。你可以根据需要注册任意多个类别对象。

要将`category`对象应用于通知，请将`category`的标识符字符串包含在你创建的所有通知的有效负载中。对于本地通知，将此字符串放在用于指定通知内容的[UNMutableNotificationContent](#)对象的[categoryIdentifier](#)属性中。对于远程通知，请使用此字符串作为有效负载的aps字典中`category`关键字的值。

`category`可以具有关联的动作，这些动作定义了在该类别的通知上显示的自定义按钮。当空间不受限制时，系统最多显示10个动作。当空间有限时，系统最多显示两个动作。

## 主题

### 创建一个通知类型

* [init(identifier: String, actions: [UNNotificationAction\], intentIdentifiers: [String], options: UNNotificationCategoryOptions)](#) 
    创建一个包含指定操作和选项的`category`对象。

* [init(identifier: String, actions: [UNNotificationAction\], intentIdentifiers: [String], hiddenPreviewsBodyPlaceholder: String, options: UNNotificationCategoryOptions)](#) 
    创建一个`category`对象，其中包含未显示预览时使用的指定操作，选项和占位符文本。

* [init(identifier: String, actions: [UNNotificationAction\], intentIdentifiers: [String], hiddenPreviewsBodyPlaceholder: String?, categorySummaryFormat: String?, options: UNNotificationCategoryOptions)](#) 
    创建一个`category`对象，其中包含指定的操作，选项，未显示预览时使用的占位符文本以及摘要格式字符串。

### 获得类型的信息

* [var identifier: String](#) 
    分配给`category`的唯一字符串。

* [var actions: \[UNNotificationAction\]](#) 
    出现此类通知时显示的动作。

* [var intentIdentifiers: \[String\]](#) 
    与该类别的通知有关的意图。

* [var hiddenPreviewsBodyPlaceholder: String](#) 
    禁用应用程序的通知预览时显示的占位符文本。

* [var categorySummaryFormat: String](#) 
    系统将类别的通知分组时使用的摘要说明的格式字符串。

### 获得类型的选项

* [var options: UNNotificationCategoryOptions](#) 
    有关如何处理此类通知的选项。

* [struct UNNotificationCategoryOptions](#) 
    指示如何处理与此类别关联的通知的常量。