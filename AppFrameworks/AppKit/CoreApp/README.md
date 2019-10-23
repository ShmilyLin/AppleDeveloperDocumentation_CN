# Core App

学习关于你用来和系统交互的对象。

--- 
## 专题

### 一、应用


#### ● [class NSApplication](./NSApplication/)

管理应用程序的主事件循环和所有应用程序对象使用的资源的对象。

#### ● [class NSRunningApplication]()

一个可以操作并为应用程序的单个实例提供信息的对象。

#### ● [protocol NSApplicationDelegate](./NSApplicationDelegate/)

[NSApplication](./NSApplication/)对象的代理协议。

#### ● [func NSApplicationMain(Int32, UnsafeMutablePointer<UnsafeMutablePointer<CChar>?>) -> Int32]()

### 二、环境

#### ● [class NSWorkspace]()

一个可以启动其他应用程序并执行各种文件处理服务的工作空间。

#### ● [AppKit版本]()

执行运行时检查以确定哪个版本的AppKit可用。

### 三、文档

#### ● [class NSDocumentController]()

管理应用程序文档的对象。

#### ● [class NSPersistentDocument]()

可以与Core Data集成的文档对象。

#### ● [class NSDocument]()

一个抽象类，用于定义macOS文档的接口。

### 四、粘贴板

#### ● [class NSPasteboard]()

与粘贴板服务器之间传输数据的对象。

#### ● [class NSPasteboardItem]()

粘贴板上的项目。

#### ● [protocol NSPasteboardReading]()

一组方法，用于定义从粘贴板初始化对象的接口。

#### ● [protocol NSPasteboardWriting]()

一组方法，用于定义用于检索可写入粘贴板的对象表示的接口。

#### ● [protocol NSPasteboardItemDataProvider]()

由粘贴板项的数据提供程序实现的一组方法，用于提供特定UTI类型的数据。

#### ● [struct NSPasteboard.ContentsOptions]()

#### ● [protocol NSPasteboardTypeOwner]() [Beta]

### 五、用户首选项

#### ● [class NSUserDefaultsController]()

一个控制器，用于从用户的默认数据库访问应用程序的用户首选项信息。

### 六、应用服务

#### ● [class NSSharingService]()

一种服务，允许用户与其他服务分享内容，例如社交媒体服务或应用程序，如Mail和Safari。

#### ● [class NSSharingServicePicker]()

用户可以选择的分享服务列表。

#### ● [protocol NSSharingServicePickerDelegate]()

用于自定义服务选择器行为的一组方法。

#### ● [protocol NSServicesMenuRequestor]()

一组支持与用户交互的可以通过分享服务进行分享的方法。

#### ● [Services Functions]()

### 七、应用帮助

#### ● [class NSHelpManager]()

用于显示应用程序在线帮助的对象。

#### ● [protocol NSUserInterfaceItemSearching]()

应用程序可以实现的一组方法，以便为自己的自定义帮助数据提供Spotlight for Help。
