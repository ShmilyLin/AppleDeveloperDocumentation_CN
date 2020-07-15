# 请求使用通知的权限

请求获得通知显示alerts，播放声音或标记应用图标的权限的响应。

## 概述

本地和远程通知通过显示alert，播放声音或标记应用程序图标来引起用户的注意。这些互动是在你的应用未运行或在后台运行时发生的。它们让用户知道你的应用程序具有相关信息供他们查看。由于用户可能认为基于通知的交互具有破坏性，因此你必须获得使用它们的许可。

### 在上下文中明确请求授权

要请求授权，请获取共享的[UNUserNotificationCenter](#)实例，然后调用其[requestAuthorization(options:completionHandler:)](#)方法。指定你的应用程序采用的所有交互类型。例如，你可以请求授权以显示alert，将横幅添加到应用程序图标或播放声音：

```Swift
let center = UNUserNotificationCenter.current()
center.requestAuthorization(options: [.alert, .sound, .badge]) { granted, error in
    
    if let error = error {
        // 在这里处理错误
    }
    
    // 根据授权启用或禁用功能。
}
```

你的应用首次发出此授权请求时，系统会提示用户批准或拒绝该请求并记录用户的响应。随后的授权请求不会提示用户。

在可以帮助用户了解你的应用为何需要授权的上下文中发出请求。在发送提醒通知的任务跟踪应用中，你可以在用户安排第一个任务后发出请求。与在首次启动时自动请求授权相比，在上下文中发送请求提供了更好的用户体验，因为用户可以更轻松地查看通知的用途。

### 使用临时授权发送测试通知

当你明确要求发送通知的权限时，用户必须先决定是允许还是拒绝权限，然后才能从你的应用程序中看到通知。 即使你在请求授权之前仔细设置了上下文，用户也可能没有足够的信息来做出决定，并且可能会拒绝授权。

使用临时授权可尝试发送一个测试通知。 然后，用户可以评估通知并决定是否对其进行授权。

系统会悄悄地发送临时通知——它们不会用声音或横幅打扰用户，也不会出现在锁定屏幕上。 相反，它们只会显示在通知中心的历史记录中。这些通知还包括按钮，提示用户保留或关闭通知。

如果用户按下“保留”按钮，则系统会提示他们在突出显示或安静显示的通知之间进行选择。 如果用户选择突出显示的通知，则你的应用将获得你在临时授权请求中的所有权限。如果用户选择接收静默通知，则系统会授权你的应用发送通知，但不会授予你的应用显示alert，播放声音或为应用图标添加标记的权限。你的通知仅出现在通知中心历史记录中。

如果用户按下“关闭”按钮，系统将在拒绝你的应用授权以发送其他通知。

要请求临时授权，请在请求允许发送通知时添加[provisional](#)选项。

```swift
let center = UNUserNotificationCenter.current()
center.requestAuthorization(options: [.alert, .sound, .badge, .provisional]) { granted, error in
    
    if let error = error {
        // Handle the error here.
    }
    
    // Provisional authorization granted.
}
```

与明确请求授权不同，此代码不会提示用户获得接收通知的权限。 相反，第一次调用此方法时，它将自动授予授权。但是，在用户明确保留或关闭通知之前，授权状态为[UNAuthorizationStatus.provisional](#)。 由于用户可以随时更改授权状态，因此你仍应在计划本地通知之前检查状态。

此外，如果你请求临时授权，则可以在应用程序首次启动时请求授权。仅在用户实际收到通知时才要求用户保留或关闭通知。

### 根据当前授权自定义通知

安排本地通知之前，请务必检查你应用的授权状态。用户可以随时更改你的应用的授权设置。他们还可以更改应用程序允许的交互类型，这可能会导致你更改应用程序发送的通知的数量或类型。

为了为你的用户提供最佳体验，请调用通知中心的[getNotificationSettings(completionHandler:)](#)方法以获取当前的通知设置。 然后根据这些设置来自定义通知。

```swift
let center = UNUserNotificationCenter.current()
center.getNotificationSettings { settings in
    guard (settings.authorizationStatus == .authorized) ||
          (settings.authorizationStatus == .provisional) else { return }

    if settings.alertSetting == .enabled {
        // 仅支持alert通知。
    } else {
        // 带有标记和声音的通知。
    }
}
```

上面的示例使用了guard条件，以防止在未授权应用程序的情况下安排通知。 然后，该代码根据所允许的交互类型来配置通知，并尽可能使用基于alert的通知。

但是，即使你的应用未获得某些互动的授权，你仍可能希望使用alert，声音和标记信息配置通知。如果你的[UNNotificationSettings](#)实例的[notificationCenterSetting](#)属性设置为[UNNotificationSetting.enabled](#)，则系统仍会在通知中心中显示alert。当你的应用程序位于前台时，通知中心delegate的[userNotificationCenter(:willPresent:withCompletionHandler:)](#)方法也会收到通知，并且仍然可以访问alert，声音或标记信息。