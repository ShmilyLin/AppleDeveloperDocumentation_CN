# NSApplication

　　管理应用程序的主事件循环和所有应用程序对象使用的资源的对象。

---
## 简介

　　每个应用程序使用一个`NSApplication`单例来控制主事件循环、保持对App的窗口和菜单的持续跟踪、将事件分发到适当的对象（即，自身或其中一个窗口）、设置自动释放池和接收App级事件的通知。一个`NSApplication`对象有一个delegate（你指定的对象），delegate中的方法在App启动或终止，切到后台或切到前台，打开用户选择的文件等等时被通知调用。通过设置delegate和实现delegate方法，你可以自定义应用程序的行为，而无需子类化`NSApplication`。在App的`main()`函数中，通过调用[share](https://developer.apple.com/documentation/appkit/nsapplication/1428360-shared)类方法来创建`NSApplication`实例。在创建应用程序对象之后，`main()`函数应该加载App的主nib文件，然后通过向应用程序对象发送`run()`消息来启动事件循环。如果在Xcode中创建一个Application项目，则会为你创建此`main()`函数。Xcode创建的`main()`函数首先调用一个名为`NSApplicationMain()`的函数，该函数在功能上类似于以下内容：

```objectivec
void NSApplicationMain(int argc, char *argv[]) {
    [NSApplication sharedApplication];
    [NSBundle loadNibNamed:@"myMain" owner:NSApp];
    [NSApp run];
}
```

　　[shared](./shared.md)类方法初始化显示环境并将App连接到窗口服务和显示服务上。`NSApplication`对象维护App使用的所有[NSWindow]()对象组成的列表，因此它可以检索任何应用程序的[NSView]()对象。[shared](./shared.md)类方法还初始化全局变量[NSApp]()，你可以使用该变量来检索`NSApplication`实例。[shared](./shared.md)只执行一次初始化，如果多次调用它，它也只返回它先前创建的App对象。

　　`NSApplication`对象单例执行 从窗口服务接收事件并将它们分发到正确的[NSResponder]()对象 的重要任务。[NSApp]()将事件转换为[NSEvent]()对象，然后将事件对象转发到受影响的[NSWindow]()对象。 所有键盘和鼠标事件都直接转到与事件关联的[NSWindow]()对象。此规则的唯一例外是在按下Command键时发生的按键事件，在这种情况下，每个[NSWindow]()对象都有机会响应该事件。当[NSWindow]()对象从[NSApp]()接收`NSEvent`对象时，它会将其分发到其视图层次结构中的对象中。

　　`NSApplication`还负责分派应用程序收到的某些Apple事件。例如，macOS会在不同时间向你的App发送Apple事件，例如应用程序启动或重新打开时。`NSApplication`通过向适当的对象发送消息来安装Apple事件处理程序来处理这些事件。你还可以使用[NSAppleEventManager]()类来注册自己的Apple事件处理程序，[applicationWillFinishLaunching(_:)]()方法通常是处理这件事情的最好的方法。有关如何处理事件以及如何修改默认行为的更多信息，包括在可编写脚本的应用程序中使用Apple事件的信息，请参阅[Cocoa脚本指南](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ScriptableCocoaApplications/SApps_intro/SAppsIntro.html#//apple_ref/doc/uid/TP40002164)中的[Cocoa应用程序如何处理Apple事件](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ScriptableCocoaApplications/SApps_handle_AEs/SAppsHandleAEs.html#//apple_ref/doc/uid/20001239)。

　　`NSApplication`类在初始化期间和事件循环内部设置`@autorelease`块——特别是在其初始化（或[shared](./shared.md)）和`run()`方法中。类似地，AppKit添加到[Bundle]()的方法在加载nib文件期间也使用`@autorelease`块。在相应的`NSApplication`和[Bundle]()方法的范围之外，无法访问这些`@autorelease`块。通常，应用程序在事件循环运行时或通过从nib文件加载对象来创建对象，因此这种缺乏访问通常不是问题。但是，如果你确实需要在`main()`函数本身中使用Cocoa类（除了加载nib文件或实例化NSApplication），你应该创建一个`@autorelease`块以包裹使用类的代码。

### Delegate和通知

　　你可以将一个delegate分配给`NSApplication`对象。delegate相应对象的某些消息。其中一些消息，例如`application(_:openFile:)`要求delegate处理一个操作。另一条消息，`applicationShouldTerminate(_:)`允许delegate确定是否应该允许应用程序退出。`NSApplication`类将这些消息直接发送到其delegate中。

　　`NSApplication`还会向应用程序的默认通知中心发布通知。任何对象都可以通过`addObserver(_:selector:name:object:) `注册到默认通知中心（[NSNotificationCenter]()类的实例）接收`NSApplication`发布的一个或多个通知。如果`NSApplication`的delegate实现了一些delegate方法，则会自动注册以接收这些通知。例如，`NSApplication`会在启动App时以及App已经启动时完成时发布通知（[willFinishLaunchingNotification]()和[didFinishLaunchingNotification]()）。delegate可以通过实现方法[applicationWillFinishLaunching(_:)]()和[applicationDidFinishLaunching(_:)]()来响应这些通知。如果delegate同时实现这两种方法，则这两个事件都会通知它。如果它只需要知道App何时完成启动，它只需要实现[applicationDidFinishLaunching(_:)]()。

### 系统服务

　　NSApplication与系统服务体系结构交互，通过“服务”菜单为您的应用程序提供服务。

### 子类化注意

　　你会发现很少真正需要创建自定义的`NSApplication`子类。与一些面向对象的库不同，Cocoa不要求你将`NSApplication`子类化为自定义App行为。相反，它为你提供了许多其他方法来自定义App。本节讨论了`NSApplication`子类化的一些可能原因以及不继承`NSApplication`的一些原因。

　　要使用`NSApplication`的自定义子类，只需将[shared](./shared.md)发送到你的子类，而不是直接发送到`NSApplication`。如果你在Xcode中创建应用程序，则可以通过将自定义App类设置为主要类来完成此操作。在Xcode中，双击 Groups and Files 列表中的app target，以打开target的“Info”窗口。然后显示窗口的“Custom macOS Application Target Properties”窗格，并将“Principal Class”字段中的“NSApplication”替换为自定义类的名称。`NSApplicationMain`函数将[shared](./shared.md)发送到主体类以获取全局应用程序实例（[NSApp]()）——在这种情况下，它将是`NSApplication`的自定义子类的实例。

> **重要**
> 
> 许多AppKit类依赖于`NSApplication`类，并且在完全初始化此类之前可能无法正常工作。 因此，你不应该尝试从`NSApplication`子类的初始化方法调用其他AppKit类的方法。

#### 重写方法

　　通常，你将`NSApplication`子类化是为对正常状态下发送到全局应用程序对象（NSApp）的消息提供你自己的特殊响应。`NSApplication`并没有子类化时你必须重写的方法。以下是四种可能你需要重写的方法：

* 如果希望应用程序以不同于默认情况的方式管理主事件循环，则重写[run()]()。（然而，这是一项至关重要且复杂的任务，你应该只有充分的理由时才这样做。）
* 如果要更改事件的分派方式或执行某些特殊事件处理，请覆盖[sendEvent(_:)]()。
* 如果要修改应用程序吸引用户注意力的方式，请覆盖[requestUserAttention(_:)]()（例如，提供Dock中弹跳应用程序图标的替代方法）。
* 重写[target(forAction:)]()以将另一个对象替换为操作消息的目标。

#### 特别注意事项

　　全局app对象在其[run()]()方法中使用`@autorelease`块; 如果重写此方法，则需要创建自己的`@autorelease`块。

　　不要重写[shared](./shared.md)。对App至关重要的行为的默认实现太复杂，无法自行复制。

#### 子类化的替代方案

　　`NSApplication`定义了许多[协议代理](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Delegation.html#//apple_ref/doc/uid/TP40008195-CH14)方法，这些方法提供了修改应用程序行为特定方面的机会。你的应用程序delegate可以实现一个或多个这些方法来实现你的设计目标，而不是创建`NSApplication`的自定义子类。 通常，比子类化`NSApplication`更好的设计是将表示应用程序特殊行为的代码放入一个或多个称为控制器的自定义对象中。控制器中定义的方法可以从小型调度程序对象调用，而不必与全局应用程序对象紧密相关。

---
## 专题

### 一、获得共享App对象

#### ● [class var shared: NSApplication](./shared.md)

　　返回App实例，如果它尚不存在则创建它。

#### ● [var NSApp: NSApplication!](./NSApp.md)

　　共享App实例的全局变量。

### 二、管理App的行为

#### ● [var delegate: NSApplicationDelegate?](./delegate.md)

　　App的delegate对象

#### ● [protocol NSApplicationDelegate](../NSApplicationDelegate/)

　　`NSApplication`的delegate对象可以实现的一组方法。

### 三、管理事件循环

#### ● [func nextEvent(matching: NSEvent.EventTypeMask, until: Date?, inMode: RunLoop.Mode, dequeue: Bool) -> NSEvent?]()

　　返回与给定掩码匹配的下一个事件，如果在指定的到期日期之前未找到此类事件，则返回`nil`。

#### ● [func discardEvents(matching: NSEvent.EventTypeMask, before: NSEvent?)]()

　　在指定事件之前删除与给定掩码匹配的所有事件。

#### ● [var currentEvent: NSEvent?]()

　　App从事件队列中检索的最后一个事件对象。

#### ● [var isRunning: Bool]()

　　一个布尔值，指示主事件循环是否正在运行。

#### ● [func run()]()

　　开始主事件循环。

#### ● [func finishLaunching()]()

　　激活App，通过[NSOpen]()打开用户默认指定的任何文件，并取消突出显示应用程序的图标。

#### ● [func stop(Any?)]()

　　停止主事件循环。

#### ● [func sendEvent(NSEvent)]()

　　将事件调度到其他对象。

#### ● [func postEvent(NSEvent, atStart: Bool)]()

　　将给定事件添加到接收者的事件队列。

#### ● [static let eventTracking: RunLoop.Mode]()

　　在以模态方式跟踪事件时，应将运行循环设置为此模式，例如鼠标拖动循环。

### 四、发送操作

#### ● [func tryToPerform(Selector, with: Any?) -> Bool]()

　　将操作消息调度到指定的目标。

#### ● [func sendAction(Selector, to: Any?, from: Any?) -> Bool]()

　　将给定的操作消息发送到给定目标。

#### ● [func target(forAction: Selector) -> Any?]()

　　返回接收给定选择器指定的操作消息的对象。

#### ● [func target(forAction: Selector, to: Any?, from: Any?) -> Any?]()

　　搜索可以接收给定选择器指定的消息的对象。

### 五、终止App

#### ● [func terminate(Any?)]()

　　终止接收器。

#### ● [func reply(toApplicationShouldTerminate: Bool)]()

　　一旦App知道它是否可以终止，则响应[NSTerminateLater]()。

### 六、激活和停用App

#### ● [var isActive: Bool]()

　　一个布尔值，指示这是否为活动中的App。

#### ● [func activate(ignoringOtherApps: Bool)]()

　　使接收器成为活动中的App。

#### ● [func deactivate()]()

　　取消激活接收器。

### 七、在登录时管理重新启动

#### ● [func disableRelaunchOnLogin()]()

　　禁用在登录时启动App。

#### ● [func enableRelaunchOnLogin()]()

　　允许在登录时重新启动应用程序。

### 八、管理远程通知

#### ● [func registerForRemoteNotifications()]()

　　注册Apple推送通知服务（APN）发送的通知。**`[Beta]`**

#### ● [func unregisterForRemoteNotifications()]()

　　取消注册从Apple推送通知服务收到的通知。

#### ● [var enabledRemoteNotificationTypes: NSApplication.RemoteNotificationType]()

　　应用程序接受的推送通知类型。

#### ● [func registerForRemoteNotifications(matching: NSApplication.RemoteNotificationType)]()

　　注册以通过Apple推送通知服务从提供商处接收指定类型的通知。

#### ● [var isRegisteredForRemoteNotifications: Bool]()

　　一个布尔值，指示应用程序是否已向Apple推送通知服务（APN）注册。**`[Beta]`**

#### ● [struct NSApplication.RemoteNotificationType]()

　　这些常量确定通过远程通知启动的应用程序是否显示角标（badge）。

### 九、管理App的外观

#### ● [var appearance: NSAppearance?]()

　　与App的窗口关联的外观。

#### ● [var effectiveAppearance: NSAppearance](./2967170-appearance.md)

　　AppKit用于绘制应用程序界面的外观。

#### ● [var currentSystemPresentationOptions: NSApplication.PresentationOptions]()

　　当前对系统有效的一组App演示选项。

#### ● [var presentationOptions: NSApplication.PresentationOptions]()

　　此App处于活动状态时应对系统有效的演示文稿选项。

#### ● [struct NSApplication.PresentationOptions]()

　　控制应用程序呈现的常量，通常用于全屏应用程序，如游戏或kiosks。

### 十、管理窗口，面板和菜单

#### ● [App Windows]()

　　显示，隐藏，最小化，排列和更新你的App的窗口。

#### ● [Modal Windows and Panels]()

　　显示模态窗口或显示标准应用程序面板之一，例如应用程序的“关于”面板。

#### ● [Menus]()

### 十一、用户界面布局方向

#### ● [var userInterfaceLayoutDirection: NSUserInterfaceLayoutDirection]()

　　用户界面的布局方向。

#### ● [enum NSUserInterfaceLayoutDirection]()

　　指定用户界面的方向流。这些常量由[userInterfaceLayoutDirection]()返回。

### 十二、访问Dock Tile

#### ● [var dockTile: NSDockTile]()

　　该应用程序的Dock Tile。

#### ● [var applicationIconImage: NSImage!]()

　　用于App图标的图像。

### 十三、自定义触控条

#### ● [func toggleTouchBarCustomizationPalette(Any?)]()

　　显示或隐藏用于自定义触控条的界面。

### 十四、管理用户关注请求

#### ● [func requestUserAttention(NSApplication.RequestUserAttentionType) -> Int]()

　　启动用户关注请求。

#### ● [enum NSApplication.RequestUserAttentionType]()

　　这些常量指定用户关注请求的严重性级别，并由[cancelUserAttentionRequest(_:)]()和[requestUserAttention(_:)]()使用。

#### ● [func cancelUserAttentionRequest(Int)]()

　　取消之前的用户关注请求。

#### ● [func reply(toOpenOrPrint: NSApplication.DelegateReply)]()

　　处理用户尝试打开或打印文件时可能发生的错误。

#### ● [enum NSApplication.DelegateReply]()

　　指示复制或打印操作是否成功、取消或失败的常量。

### 十五、提供帮助信息

#### ● [func registerUserInterfaceItemSearchHandler(NSUserInterfaceItemSearching)]()

　　注册一个向你的应用提供帮助数据的对象。

#### ● [func searchString(String, inUserInterfaceItemString: String, range: NSRange, found: UnsafeMutablePointer<NSRange>?) -> Bool]()

　　在用户界面中搜索字符串。

#### ● [func unregisterUserInterfaceItemSearchHandler(NSUserInterfaceItemSearching)]()

　　取消注册向你的应用提供帮助数据的对象。

#### ● [func showHelp(Any?)]()

　　如果你的项目已正确注册，并且已在属性列表中设置了必要的键，则此方法将启动帮助查看器并显示应用程序帮助手册的第一页。

#### ● [func activateContextHelpMode(Any?)]()

　　将接收器置于上下文相关的帮助模式中。

#### ● [var helpMenu: NSMenu?]()

　　应用使用的帮助菜单。

### 十六、提供服务

#### ● [func validRequestor(forSendType: NSPasteboard.PasteboardType?, returnType: NSPasteboard.PasteboardType?) -> Any?]()

　　指示接收器是否可以发送和接收指定的粘贴板类型。

#### ● [var servicesProvider: Any?]()

　　提供当前应用程序在其他应用程序的“服务”菜单中公布的服务的对象。

### 十七、确定对键盘的访问权限

#### ● [var isFullKeyboardAccessEnabled: Bool]()

　　一个布尔值，指示是否在键盘首选项窗格中启用全键盘访问。

### 十八、隐藏App

#### ● [func hideOtherApplications(Any?)]()

　　隐藏除接收器之外的所有App。

#### ● [func unhideAllApplications(Any?)]()

　　取消隐藏所有App，包括接收器。

### 十九、管理线程

#### ● [class func detachDrawingThread(Selector, toTarget: Any, with: Any?)]()

　　根据指定的目标和选择器创建并执行新线程。

### 二十、记录例外

#### ● [func reportException(NSException)]()

　　通过调用[NSLog()]()来记录给定的异常。

### 二十一、配置激活策略

#### ● [func activationPolicy() -> NSApplication.ActivationPolicy]()

　　返回App的激活策略。

#### ● [func setActivationPolicy(NSApplication.ActivationPolicy) -> Bool]()

　　尝试修改App的激活策略。

#### ● [enum NSApplication.ActivationPolicy]()

　　激活策略（由[activationPolicy]()使用），用于控制是否激活以及如何激活App。

### 二十二、编写应用程序脚本

#### ● [var orderedDocuments: [NSDocument]]()

　　根据相关窗口的前后排序排列的文档对象数组。

#### ● [var orderedWindows: [NSWindow]]()

　　一系列窗口对象根据它们在屏幕上的前后排序排列。

#### ● [func application(NSApplication, delegateHandlesKey: String) -> Bool]()

　　在执行`get`或`set`脚本命令期间由Cocoa的内置脚本支持发送，以查明delegate是否可以处理指定key-value的key的操作。

### 二十三、通知

　　这些通知适用于`NSApplication`。 有关其他类似的通知，请参阅[NSWorkspace]()中的通知。

#### ● [class let didBecomeActiveNotification: NSNotification.Name]()

　　在App变为活动状态后立即发送通知。

#### ● [class let didChangeScreenParametersNotification: NSNotification.Name]()

　　在更改连接到计算机的显示器配置时发送通知。

#### ● [class let didFinishLaunchingNotification: NSNotification.Name]()

　　在[finishLaunching()]()方法的结束时发送通知，表示App已完成启动并准备好运行。

#### ● [class let didHideNotification: NSNotification.Name]()

　　在[hide(_:)]()方法的结束时发送通知，表示该App现在已隐藏。

#### ● [class let didResignActiveNotification: NSNotification.Name]()

　　App的活动状态变为放在其他App后面时立即发送通知。

#### ● [class let didUnhideNotification: NSNotification.Name]()

　　在[unhideWithoutActivation()]()方法的结束时发送通知，表示该App现在可见。

#### ● [class let didUpdateNotification: NSNotification.Name]()

　　在[updateWindows()]()方法的结束时发送通知，表示App已完成更新其窗口。

#### ● [class let willBecomeActiveNotification: NSNotification.Name]()

　　在App变为活动状态之前立即发送通知。

#### ● [class let willFinishLaunchingNotification: NSNotification.Name]()

　　在[finishLaunching()]()方法开始时发送通知，表示App已完成其初始化过程并即将完成启动。

#### ● [class let willHideNotification: NSNotification.Name]()

　　在[hide(_:)]()方法开始时发送通知，表示该App即将被隐藏。

#### ● [class let willResignActiveNotification: NSNotification.Name]()

　　在App的活动状态变为放在其他应用程序前面时立即发送通知。

#### ● [class let willTerminateNotification: NSNotification.Name]()

　　由[terminate(_:)]()方法发送通知，表明App将终止。

#### ● [class let willUnhideNotification: NSNotification.Name]()

　　在[unhideWithoutActivation()]()方法开始时发送通知，表示App即将变为可见。

#### ● [class let willUpdateNotification: NSNotification.Name]()

　　在[updateWindows()]()方法开始时发送通知，表示该App即将更新其窗口。

#### ● [class let didFinishRestoringWindowsNotification: NSNotification.Name]()

　　App完成恢复窗口时发送通知。

#### ● [class let didChangeOcclusionStateNotification: NSNotification.Name]()

　　App的遮挡状态发生变化时发送通知。

### 二十四、加载Cocoa Bundles

#### ● [static func loadApplication()]()

### 二十五、结构

#### ● [struct NSApplication.ActivationOptions]()

　　其下标志用于[activate(options:)]()。

---
## 其他内容

### 应用

#### ● [class NSRunningApplication]()

　　一个可以操作并为应用程序的单个实例提供信息的对象。

#### ● [protocol NSApplicationDelegate](../NSApplicationDelegate/)

　　[NSApplication](./NSApplication/)对象的代理协议。

#### ● [func NSApplicationMain(Int32, UnsafeMutablePointer<UnsafeMutablePointer<CChar>?>) -> Int32]()



---

> **Bate软件**
> 
> 本文档包含有关正在开发的API或技术的初步信息。这些信息可能会发生变化，根据本文档实施的软件应使用最终确定的操作系统软件进行测试。