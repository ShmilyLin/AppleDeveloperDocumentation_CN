# setNotificationCategories(_:)

注册你的应用的通知类型及其支持的自定义操作。

## 声明

```swift
func setNotificationCategories(_ categories: Set<UNNotificationCategory>)
```

## 参数

* `categories`一组[UNNotificationCategory](#)对象，每个对象都包含用通知界面显示的操作。此参数必须包含你应用支持的所有类别。

## 说明

在启动时调用此方法，以注册你的应用可操作的通知类型。 此方法可一次注册所有类别，将所有先前注册的类别替换为`categories`参数中的新类别。通常，只调用一次此方法。

`categories`参数中的每个对象都包含一个字符串，用于标识通知的类型。它还包含用户可以响应该类型的通知而执行的一个或多个自定义操作。当系统显示通知alert时，它将在通知有效负载中查找类别对象中的标识符字符串之一。 如果找到一个，则会为与该类别对象关联的每个动作添加用户可选按钮。轻按按钮会将选定的操作通知你的应用程序，而无需将应用程序置于前台。