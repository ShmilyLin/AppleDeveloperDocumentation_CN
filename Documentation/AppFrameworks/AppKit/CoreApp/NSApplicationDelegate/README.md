# NSApplicationDelegate

[NSApplication](../NSApplication)的delegate对象可以实现的一组方法。

> SDK : macOS 10.6+

---
## 专题

### 一、启动App

#### ● [func applicationWillFinishLaunching(Notification)](./applicationWillFinishLaunching.md)

在App对象初始化之前由默认通知中心（default notification center）发送。

#### ● [func applicationDidFinishLaunching(Notification)](./applicationDidFinishLaunching.md)

在App启动并初始化之后，但在收到第一个事件之前，由默认通知中心（default notification center）发送。

#### ● [NSApplicationDidFinishLaunching User Info Keys](./NSApplicationDidFinishLaunchingUserInfoKeys/)

其下的常量定义了[didFinishLaunchingNotification]()中可以存在的key。

### 二、管理活动状态

#### ● [func applicationWillBecomeActive(Notification)](./applicationWillBecomeActive.md)

在App变为活动状态之前由默认通知中心（default notification center）发送。

#### ● [func applicationDidBecomeActive(Notification)](./applicationDidBecomeActive.md)

在App变为活动状态后立即由默认通知中心（default notification center）发送。

#### ● [func applicationWillResignActive(Notification)](./applicationWillResignActive.md)

在App变为不活动状态之前，由默认通知中心（default notification center）发送。

#### ● [func applicationDidResignActive(Notification)](./applicationDidResignActive.md)

在App变为不活动状态后，由默认通知中心（default notification center）发送。

### 三、终止App

#### ● [func applicationShouldTerminate(NSApplication) -> NSApplication.TerminateReply](./applicationShouldTerminate.md)

发送通知给delegate表示该App即将终止。

#### ● [func applicationShouldTerminateAfterLastWindowClosed(NSApplication) -> Bool](./applicationShouldTerminateAfterLastWindowClosed.md)

当用户关闭App打开的最后一个窗口时调用。

#### ● [func applicationWillTerminate(Notification)](./applicationWillTerminate.md)

在App终止之前由默认通知中心（default notification center）发送。

#### ● [enum NSApplication.TerminateReply](./NSApplicationTerminateReply/)

delegate方法[applicationShouldTerminate(_:)](./applicationShouldTerminate.md)使用的常量，来确定应用程序是否应终止。

### 四、隐藏App

#### ● [func applicationWillHide(Notification)](./applicationWillHide.md)

在隐藏App之前，由默认通知中心（default notification center）发送。

#### ● [func applicationDidHide(Notification)](./applicationDidHide.md)

在隐藏App之后，由默认通知中心（default notification center）发送。

#### ● [func applicationWillUnhide(Notification)](./applicationWillUnhide.md)

在取消隐藏App之前，由默认通知中心（default notification center）发送。

#### ● [func applicationDidUnhide(Notification)](./applicationDidUnhide.md)

在取消隐藏App之后，由默认通知中心（default notification center）发送。

### 五、管理窗口

#### ● [func applicationWillUpdate(Notification)](./applicationWillUpdate.md)

在App对象更新其窗口之前，由默认通知中心（default notification center）发送。

#### ● [func applicationDidUpdate(Notification)](./applicationDidUpdate.md)

在App对象更新其窗口之后，由默认通知中心（default notification center）发送。

#### ● [func applicationShouldHandleReopen(NSApplication, hasVisibleWindows: Bool) -> Bool](./applicationShouldHandleReopenHasVisibleWindows.md)

在默认行为之前由App发送给delegate以重新打开（rapp）AppleEvents。

### 六、管理程序坞菜单

#### ● [func applicationDockMenu(NSApplication) -> NSMenu?](./applicationDockMenu.md)

允许delegate动态地为App提供程序坞菜单。

### 七、显示错误

#### ● [func application(NSApplication, willPresentError: Error) -> Error](./applicationWillPresentError.md)

在指定的App向用户显示错误消息之前发送给delegate。

### 八、管理屏幕

#### ● [func applicationDidChangeScreenParameters(Notification)](./applicationDidChangeScreenParameters.md)

当更改连接到计算机的显示配置时（通过编程方式或用户更改“显示”控制面板中的设置），由默认通知中心（default notification center）发送。

### 九、保持用户活动

#### ● [func application(NSApplication, willContinueUserActivityWithType: String) -> Bool](./applicationWillContinueUserActivityWithType.md)

告诉delegate用户想要在你的应用中继续活动。

#### ● [func application(NSApplication, continue: NSUserActivity, restorationHandler: ([Any]) -> Void) -> Bool](./applicationContinueRestorationHandler.md)

告诉delegate，可以使用继续活动的数据。

#### ● [func application(NSApplication, didFailToContinueUserActivityWithType: String, error: Error)]()

告诉delegate该活动无法继续。

#### ● [func application(NSApplication, didUpdate: NSUserActivity)]()

告诉delegate，用户活动对象已更新。

### 十、处理推送通知

#### ● [func application(NSApplication, didRegisterForRemoteNotificationsWithDeviceToken: Data)](./applicationDidRegisterForRemoteNotificationsWithDeviceToken.md)

Apple推送服务成功完成注册过程后发送给delegate。

#### ● [func application(NSApplication, didFailToRegisterForRemoteNotificationsWithError: Error)]()

Apple推送服务无法成功完成注册过程时发送给delegate。

#### ● [func application(NSApplication, didReceiveRemoteNotification: [String : Any])]()

当正在运行的App收到远程通知时发送给delegate。

### 十一、处理CloudKit邀请

#### ● [func application(NSApplication, userDidAcceptCloudKitShareWith: CKShareMetadata)]()

告知delegate该用户已接受与你的应用关联的CloudKit共享邀请。

### 十二、打开文件

#### ● [func application(NSApplication, open: [URL])]()

#### ● [func application(NSApplication, openFile: String) -> Bool]()

告诉delegate打开一个文件。

#### ● [func application(Any, openFileWithoutUI: String) -> Bool]()

告诉delegate以编程方式打开文件。

#### ● [func application(NSApplication, openTempFile: String) -> Bool]()

告诉delegate打开一个临时文件。

#### ● [func application(NSApplication, openFiles: [String])]()

告诉delegate打开多个文件。

#### ● [func applicationOpenUntitledFile(NSApplication) -> Bool]()

告诉delegate打开一个无标题文件。

#### ● [func applicationShouldOpenUntitledFile(NSApplication) -> Bool]()

在打开无标题文件之前立即调用。

### 十三、打印

#### ● [func application(NSApplication, printFile: String) -> Bool]()

当用户使用`-NSPrint`选项在命令行上启动应用程序时发送。

#### ● [func application(NSApplication, printFiles: [String], withSettings: [NSPrintInfo.AttributeKey : Any], showPrintPanels: Bool) -> NSApplication.PrintReply]()

打印一组文件。

#### ● [enum NSApplication.PrintReply]()

delegate方法[application(_:printFiles:withSettings:showPrintPanels:)]()返回的常量。

### 十四、恢复APP状态

#### ● [func application(NSApplication, didDecodeRestorableState: NSCoder)]()

告诉delegate，应用程序已从给定的归档器中提取其可恢复状态。

#### ● [func application(NSApplication, willEncodeRestorableState: NSCoder)]()

告诉delegate，应用程序将编码在应用程序启动期间保留的任何应用程序状态。

### 十五、处理对遮挡状态的更改

#### ● [func applicationDidChangeOcclusionState(Notification)]()

告诉delegate应用程序的遮挡状态已更改。

### 十六、实例方法

#### ● [func application(NSApplication, delegateHandlesKey: String) -> Bool]() `[Beta]`

---
## 关系

### 继承自

[NSObjectProtocol]()

---
## 其他内容

### 应用

#### ● [class NSApplication](../NSApplication/)

管理应用程序的主事件循环和所有应用程序对象使用的资源的对象。

#### ● [class NSRunningApplication]()

一个可以操作并为应用程序的单个实例提供信息的对象。

#### ● [func NSApplicationMain(Int32, UnsafeMutablePointer<UnsafeMutablePointer<CChar>?>) -> Int32]()

