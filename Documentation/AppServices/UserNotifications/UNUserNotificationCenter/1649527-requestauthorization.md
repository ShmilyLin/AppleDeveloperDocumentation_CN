# requestAuthorization(options:completionHandler:)

当本地和远程通知传递到用户的设备时，请求与用户进行交互的授权。

## 声明

```swift
func requestAuthorization(options: UNAuthorizationOptions = [], 
        completionHandler: @escaping (Bool, Error?) -> Void)
```

## 参数

* `options`
    你的应用请求的授权选项。你可以组合可用的常量来请求多个类型的授权。仅请求你计划使用的授权选项。有关可能值的列表，请参见[UNAuthorizationOptions]()。

* `completionHandler`
    与结果异步执行的代码块。该代码块可以在后台线程上执行。该代码块没有返回值，并具有以下参数：
    * `granted`
        一个布尔值，指示是否已授权。当授予一个或多个类型时，此参数的值为`true`。 当拒绝所有类型的授权时，该值为`false`。
    * `error`
        包含错误信息的对象；如果未发生错误，则为`nil`。

## 说明

如果你的应用的本地或远程通知涉及用户交互，则你必须请求系统授权才能执行这些交互。互动包括显示alert，播放声音或标记应用程序图标。

> 注意
>
> 在计划任何本地通知之前和向Apple Push Notification服务注册之前，请始终调用此方法。 在帮助用户了解你的应用为何需要授权的上下文中执行此操作，如[请求使用通知的权限](../AskingPermissionToUseNotifications.md)中所述。

你的应用程序第一次调用该方法时，系统会提示用户授权所请求的交互。用户可以授予或拒绝授权，并且系统存储用户的响应，以便随后对该方法的调用时不会再次提示用户。在确定授权状态之后，用户通知中心对象将执行`completionHandler`参数中的代码块。 使用该代码块中可以对你应用的行为进行任何调整。例如，如果授权被拒绝，则你可以通知远程通知服务器不要将通知发送到用户的设备。

用户可以随时在系统设置中更改允许的交互。使用[getNotificationSettings(completionHandler:)](#)方法来确定你的应用当前允许哪些交互。

