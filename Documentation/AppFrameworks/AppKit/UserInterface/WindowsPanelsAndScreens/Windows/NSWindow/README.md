# NSWindow

应用在屏幕上显示的窗口。

## 定义

```swift
class NSWindow : NSResponder
```

## 概述

一个NSWindow对象最多对应一个屏幕窗口。窗口有两个主要功能，一是提供一个可以放置视图的区域，二是接收用户通过使用鼠标和键盘进行的操作而引发的事件，并将这些事件分配给对应的视图。

> 注意
> 
> 尽管NSWindow类从NSResponder继承了NSCoding协议，但该类不支持编写。存在对存档器的旧式支持，但是不建议使用它，并且可能无法使用。任何尝试使用键控编码对象归档或取消归档窗口对象的尝试都会引发invalidArgumentException异常。

## 主题

### 创建窗口

* [init(contentViewController: NSViewController)]()

    创建一个带标题的窗口，其中包含指定的内容视图控制器。

* [init(contentRect: NSRect, styleMask: NSWindow.StyleMask, backing: NSWindow.BackingStoreType, defer: Bool)](./1419477-init.md)

    使用指定值创建一个窗口。

* [init(contentRect: NSRect, styleMask: NSWindow.StyleMask, backing: NSWindow.BackingStoreType, defer: Bool, screen: NSScreen?)]()

    使用指定的值初始化分配的窗口。

### 配置窗口

* [func toggleFullScreen(Any?)]()

    窗口进入或退出全屏模式。

* [var worksWhenModal: Bool]()

    一个布尔值，表示即使正在模态运行其他某个窗口，该窗口是否也能够接收键盘和鼠标事件。

* [var alphaValue: CGFloat]()

    窗口的透明度。

* [var backgroundColor: NSColor!]()

    窗口的背景颜色。

* [var colorSpace: NSColorSpace?]()

    窗口的色域。

* [var contentView: NSView?]()

    窗口的内容视图，即窗口视图层次结构中可访问性最高的[NSView]()对象。

* [var contentViewController: NSViewController?]()

    窗口的主内容视图控制器。

* [var canHide: Bool]()

    一个布尔值，表示当窗口的应用程序变为隐藏状态时（在执行`NSApplication`的[hide(_ :)]()方法期间）是否可以隐藏该窗口。

* [var isOnActiveSpace: Bool]()

    一个布尔值，表示窗口是否在当前活动空间上。

* [var hidesOnDeactivate: Bool]()

    一个布尔值，表示当窗口的应用程序变为非活动状态时是否将其从屏幕上删除。

* [var collectionBehavior: NSWindow.CollectionBehavior]()

    一个值，用于标识窗口在窗口集合中的行为。

* [var isOpaque: Bool]()

    一个布尔值，表示窗口是否不透明。

* [var hasShadow: Bool]()

    一个布尔值，表示窗口是否显示阴影。

* [func invalidateShadow()]()

    使窗口阴影无效，以便根据当前窗口形状重新计算它。

* [func autorecalculatesContentBorderThickness(for: NSRectEdge) -> Bool]()

    指示窗口是否自动计算给定边框的厚度。

* [func setAutorecalculatesContentBorderThickness(Bool, for: NSRectEdge)]()

    指定窗口是否自动计算给定边框的厚度。

* [func contentBorderThickness(for: NSRectEdge) -> CGFloat]()

    指示窗口给定边框的厚度。

* [func setContentBorderThickness(CGFloat, for: NSRectEdge)]()

    指定窗口给定边框的厚度。

* [var delegate: NSWindowDelegate?]()

    窗口的代理对象。

* [var preventsApplicationTerminationWhenModal: Bool]()

    一个布尔值，指示窗口是否为模态时阻止应用程序终止。

### 访问窗口信息

* [class var defaultDepthLimit: NSWindow.Depth]()

    返回NSWindow实例的默认深度限制。

* [var windowNumber: Int]()

    窗口的窗口设备中的窗口号。

* [class func windowNumbers(options: NSWindow.NumberListOptions) -> [NSNumber]?]()
Returns the window numbers for all visible windows satisfying the specified options.

* [var deviceDescription: [NSDeviceDescriptionKey : Any]]()
A dictionary containing information about the window’s resolution, such as color, depth, and so on.

* [struct NSDeviceDescriptionKey]()
These constants are the keys for device description dictionaries used by 
deviceDescription
.

* [var canBecomeVisibleWithoutLogin: Bool]()
A Boolean value that indicates whether the window can be displayed at the login window.

* [var sharingType: NSWindow.SharingType]()
A Boolean value that indicates the level of access other processes have to the window’s content.

* [var backingType: NSWindow.BackingStoreType]()
The window’s backing store type.

* [var depthLimit: NSWindow.Depth]()
The depth limit of the window.

* [var hasDynamicDepthLimit: Bool]()
A Boolean value that indicates whether the window’s depth limit can change to match the depth of the screen it’s on.

### 获取布局信息

### 管理窗口

### 管理`Sheet`

* [var attachedSheet: NSWindow?](./1419467-attachedsheet.md)

粘贴到`窗口`的`Sheet`。

* [var isSheet: Bool](./1419364-issheet.md)

一个布尔值，指示`窗口`是否曾经作为`模态Sheet`运行

* [func beginSheet(NSWindow, completionHandler: ((NSApplication.ModalResponse) -> Void)?)](./1419653-beginsheet.md)

开始文档模式的会话并呈现（或呈现队列）`Sheet`。

* [func beginCriticalSheet(NSWindow, completionHandler: ((NSApplication.ModalResponse) -> Void)?)](./1419198-begincriticalsheet.md)

启动文档模式会话并显示指定的`Critical Sheet`。

* [func endSheet(NSWindow)](./1419318-endsheet.md)

结束文档模式会话并关闭指定的`Sheet`。

* [func endSheet(NSWindow, returnCode: NSApplication.ModalResponse)](./1419497-endsheet.md)

结束文档模式会话并关闭指定的`Sheet`。

* [var sheetParent: NSWindow?](./1419052-sheetparent.md)

`Sheet`连接到的`窗口`。

* [var sheets: [NSWindow]](./1419765-sheets.md)

当前连接到`窗口`的`Sheet`数组。

### 窗口大小

### 内容大小

### 管理窗口的层

### 管理窗口可见性和遮挡状态

* [var isVisible: Bool](./1419132-isvisible.md)

    一个布尔值，指示该窗口在屏幕上是否可见（即使其他窗口遮挡了该窗口）。

* [var occlusionState: NSWindow.OcclusionState](./1419321-occlusionstate.md)

    窗口的遮挡状态。

### 在用户默认设置下管理窗口框架

### 管理Key状态

### 管理Main状态

### 管理工具栏

### 管理连接的窗口

### 管理窗口缓冲区

### 管理默认按钮

* [var defaultButtonCell: NSButtonCell?]()

    当窗口接收到Return（或Enter）按键事件时，该按钮单元的执行就像单击一样。

* [func enableKeyEquivalentForDefaultButtonCell()]()

    重新启用默认的按钮单元格等效键，以便在用户按下Return键（或Enter键）时执行单击。

* [func disableKeyEquivalentForDefaultButtonCell()]()

    禁用默认的按钮单元格等效键，因此当用户按下Return键（或Enter键）时，它不会执行单击。

### 管理字段编辑器

### 管理窗口菜单

* [var isExcludedFromWindowsMenu: Bool]()

一个布尔值，指示该Window是否从应用程序的Windows菜单中排除。

### 管理光标矩形

### 管理标题栏

* [class func standardWindowButton(NSWindow.ButtonType, for: NSWindow.StyleMask) -> NSButton?]()

    返回给定标准窗口按钮的新实例，其大小适合给定窗口样式。

* [func standardWindowButton(NSWindow.ButtonType) -> NSButton?]()

    返回窗口视图层次结构中给定窗口按钮类型的窗口按钮。

* [var showsToolbarButton: Bool](./1419196-showstoolbarbutton.md)

    一个布尔值，指示当前是否显示`工具栏`控制按钮。

* [var titlebarAppearsTransparent: Bool](./1419167-titlebarappearstransparent.md)

    一个布尔值，指示`标题栏`是否绘制其背景。

### 管理工具栏标题栏区域

### 管理窗口标签

### 管理工具提示

### 处理事件

### 管理响应者

### 管理Key视图循环

### 处理键盘事件

### 处理鼠标事件

### 处理窗口还原

* [var isRestorable: Bool]()

    一个布尔值，指示在应用程序启动之间是否保留窗口配置。

* [var restorationClass: NSWindowRestoration.Type?]()
The restoration class associated with the window.

* [func disableSnapshotRestoration()]()
Disable snapshot restoration.

* [func enableSnapshotRestoration()]()
Enable snapshot restoration.

### 包围图操作

### 绘制窗口

### 窗口动画

### 更新窗口

### 拖曳项目

### 访问编辑状态

### 转换座标

### 管理标题

### 访问屏幕信息

### 移动窗口

### 正在关闭窗口

### 正在最小化窗口

### 获取Dock Tile

### 窗口输出

### 提供服务

### 触发基于约束的布局

### 调试基于约束的布局

### 基于约束的布局

### 使用Carbon

### 使用Window Depths

### 获取有关脚本属性的信息

### 设置脚本属性

### 处理脚本命令

### 使用Ordered Indices

### 常量

* [struct NSWindow.StyleMask](./stylemask.md)

    这些常量指定窗口的样式，并且可以使用C位或运算符进行组合。

* [enum NSWindow.SelectionDirection]()
These constants specify the direction a window is currently using to change the key view. They’re used by 
keyViewSelectionDirection
.

* [enum NSWindow.ButtonType]()
These constants provide a way to access standard title bar buttons:

* [NSRunLoop—Ordering Modes for NSWindow]()
These constants are passed to NSRunLoop's 
perform(_:target:argument:order:modes:)
.

* [enum NSWindow.Depth]()
This type represents the depth, or amount of memory, devoted to a single pixel in a window or screen. A depth of 0 indicates default depth. Window depths should not be made persistent as they will not be the same across systems.

* [enum NSWindow.BackingStoreType](./backingstoretype.md)

    这些常量指定窗口设备如何在窗口中完成绘制。

* [enum NSWindow.OrderingMode]()
These constants let you specify how a window is ordered relative to another window. For more information, see 
order(_:relativeTo:)
.

* [enum NSWindow.SharingType]()
The following constants and the related data type represent the access levels other processes can have to a window’s content.

* [struct NSWindow.NumberListOptions]()
The options that may be passed to the 
windowNumbers(options:)
 method.

* [enum NSWindow.AnimationBehavior]()
These constants control the automatic window animation behavior used when the 
orderFront(_:)
 or 
orderOut(_:)
 methods are called.

* [struct NSWindow.CollectionBehavior]()
Window collection behaviors related to Exposé and Spaces.

* [struct NSWindow.OcclusionState](./occlusionstate.md)

    指定窗口遮挡状态。

* [enum NSWindow.TitleVisibility]()
Specifies the appearance of the window’s title bar area.

* [enum NSWindow.UserTabbingPreference]()
enum NSWindow.TabbingMode
The preferred tabbing behavior of a window.

* [NSWindowDidChangeBackingPropertiesNotification User Info Properties]()
These constants are values that are returned in the 
userInfo
 dictionary of the 
didChangeBackingPropertiesNotification
.

### 通知

* [class let didBecomeKeyNotification: NSNotification.Name]()
Posted whenever an NSWindow object becomes the key window.

* [class let didBecomeMainNotification: NSNotification.Name]()
Posted whenever an NSWindow object becomes the main window.

* [class let didChangeScreenNotification: NSNotification.Name]()
Posted whenever a portion of an NSWindow object’s frame moves onto or off of a screen.

* [class let didChangeScreenProfileNotification: NSNotification.Name]()
Posted whenever the display profile for the screen containing the window changes.

* [class let didDeminiaturizeNotification: NSNotification.Name]()
Posted whenever an NSWindow object is deminimized.

* [class let didEndSheetNotification: NSNotification.Name]()
Posted whenever an NSWindow object closes an attached sheet.

* [class let didEndLiveResizeNotification: NSNotification.Name]()
Posted after the user resizes a window.

* [class let didExposeNotification: NSNotification.Name]()
Posted whenever a portion of a nonretained NSWindow object is exposed, whether by being ordered in front of other windows or by other windows being removed from in front of it.

* [class let didMiniaturizeNotification: NSNotification.Name]()
Posted whenever an NSWindow object is minimized.

* [class let didMoveNotification: NSNotification.Name]()
Posted whenever an NSWindow object is moved.

* [class let didResignKeyNotification: NSNotification.Name]()
Posted whenever an NSWindow object resigns its status as key window.

* [class let didResignMainNotification: NSNotification.Name]()
Posted whenever an NSWindow object resigns its status as main window.

* [class let didResizeNotification: NSNotification.Name]()
Posted whenever an NSWindow object’s size changes.

* [class let didUpdateNotification: NSNotification.Name]()
Posted whenever an NSWindow object receives an 
update()
 message.

* [class let willBeginSheetNotification: NSNotification.Name]()
Posted whenever an NSWindow object is about to open a sheet.

* [class let willCloseNotification: NSNotification.Name]()
Posted whenever an NSWindow object is about to close.

* [class let willMiniaturizeNotification: NSNotification.Name]()
Posted whenever an NSWindow object is about to be minimized.

* [class let willMoveNotification: NSNotification.Name]()
Posted whenever an NSWindow object is about to move.

* [class let willStartLiveResizeNotification: NSNotification.Name]()
Posted before the user resizes a window.

* [class let willEnterFullScreenNotification: NSNotification.Name]()
Posted when the window will enter full screen mode.

* [class let didEnterFullScreenNotification: NSNotification.Name]()
Posted when the window entered full screen mode.

* [class let willExitFullScreenNotification: NSNotification.Name]()
Posted when the window will exit full screen mode.

* [class let didExitFullScreenNotification: NSNotification.Name]()
Posted when the window did exit full screen mode.

* [class let willEnterVersionBrowserNotification: NSNotification.Name]()
Posted when the window will enter version browser mode.

* [class let didEnterVersionBrowserNotification: NSNotification.Name]()
Posted when the window will enter version browser mode.

* [class let willExitVersionBrowserNotification: NSNotification.Name]()
Posted when the window will exit version browser mode.

* [class let didExitVersionBrowserNotification: NSNotification.Name]()
Posted when the window did exit version browser mode.

* [class let didChangeBackingPropertiesNotification: NSNotification.Name]()
Posted when the window backing properties change.

* [class let didChangeOcclusionStateNotification: NSNotification.Name]()
Posted when the window’s occlusion state changes.

### 实例属性

* [var appearanceSource: NSAppearanceCustomization!]()
* [var isFloatingPanel: Bool]()
* [var isMiniaturizable: Bool]()
* [var isModalPanel: Bool]()
* [var isResizable: Bool]()
* [var styleMask: NSWindow.StyleMask]()
* [var windowTitlebarLayoutDirection: NSUserInterfaceLayoutDirection]()
* [var isZoomable: Bool]()

### 实例方法

* [func canRepresent(NSDisplayGamut) -> Bool]()
* [func convertPoint(fromScreen: NSPoint) -> NSPoint]()
* [func convertPoint(toScreen: NSPoint) -> NSPoint]()
* [func convertPointFromBacking(NSPoint) -> NSPoint]()
* [func convertPointToBacking(NSPoint) -> NSPoint]()
* [func mergeAllWindows(Any?)]()
* [func setDynamicDepthLimit(Bool)]()
* [func setFrameAutosaveName(NSWindow.FrameAutosaveName) -> Bool]()