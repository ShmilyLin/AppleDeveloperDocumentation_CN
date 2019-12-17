# NSWindowController

管理`窗口`的控制器，通常是存储在`nib`文件中的`窗口`。

## 定义

```swift
class NSWindowController : NSResponder
```

## 概述

管理`窗口`需要以下：

* 加载并显示`窗口`
* 在适当的时候关闭`窗口`
* 自定义`窗口`标题
* 将`窗口`的框架（大小和位置）存储在默认数据库中
* 将`窗口`与App的其他`文档窗口`相关联

`窗口控制器`可以自己管理`窗口`，也可以作为AppKit基于文档的体系结构中的角色扮演者来管理`窗口`，该体系结构还包括[NSDocument]()和[NSDocumentController]()对象。在这种体系结构中，`窗口控制器`由“document”（NSDocument子类的实例）创建和管理，并依次保留对文档的引用。

`窗口控制器`和`nib`文件之间的关联很重要。尽管`窗口控制器`可以管理以编程方式创建的`窗口`，但是通常它会在`nib`文件中管理`窗口`。`nib`文件可以包含其他顶级对象，包括其他`窗口`，但是`窗口控制器`对`主窗口`负责。`窗口控制器`通常是`nib`文件的所有者，即使它是基于文档的App的一部分也是如此。无论文件的所有者是谁，`窗口控制器`都负责释放加载的`nib`文件中的所有顶级对象。

对于简单的文档（即，只有一个包含`窗口`的`nib`文件的文档），你不需要使用`NSWindowController`进行任何操作，AppKit会为你创建一个。但是，如果默认的`窗口控制器`不满足你的需求，则可以创建[NSWindowController]()的自定义子类。对于具有多个`窗口`或`面板`的文档，你的文档必须创建[NSWindowController]()（或[NSWindowController]()的自定义子类）的单独实例，每个`窗口`或`面板`一个。一个示例CAD应用程序具有不同的`窗口`，分别用于绘制对象的侧视图，俯视图和正视图。你在[NSDocument]()子类中的操作确定使用默认的[NSWindowController]()还是单独创建和配置的[NSWindowController]()对象。

### 子类化NSWindowController

当你想增加默认行为时，应该创建`NSWindowController`的子类，例如为`窗口`赋予自定义标题或在加载`窗口`之前执行一些设置任务。在你的子类的初始化方法中，请确保在用`super`调用`initWithWindowNibName:...`初始化程序或[init(window :)]()初始化程序。选择的初始化程序取决于`window`对象是源自`nib`文件还是以编程方式创建。

你还可以实现`NSWindowController`子类，以避免在实例化`窗口控制器`时要求客户端代码获取相应的`nib`文件名并将其传递给[init(windowNibName:)]()或[init(windowNibName:owner:)]()。最好的方法是重写`windowNibName`以返回`nib`的文件名，并通过将`nil`传递给[init(window:)]()来实例化`窗口控制器`。使用[init(window:)]()指定的初始值设定项可简化对Swift初始值设定项的要求。

通常，你需要重写表1中列出的方法之一。

| 方法名 | 说明 |
|:---|:---|
| [windowWillLoad()]() | 在加载nib文件之前执行一些任务 |
| [windowDidLoad()]() | 在加载nib文件之后执行一些任务 |
| [windowTitle(forDocumentDisplayName:)] | 自定义窗口标题 |

你也可以重写[loadWindow()]()以获得不同的`nib`查询或`nib`加载行为，尽管通常无需这样做。

## 主题

### 初始化`窗口控制器`

init(window: NSWindow?)
Returns a window controller initialized with a given window.

init(windowNibName: NSNib.Name)
Returns a window controller initialized with a nib file.

init(windowNibName: NSNib.Name, owner: Any)
Returns a window controller initialized with a nib file and a specified owner for that nib file.

init(windowNibPath: String, owner: Any)
Returns a window controller initialized with a nib file at an absolute path and a specified owner.

### 加载并显示`窗口`

func loadWindow()
Loads the receiver’s window from the nib file.

func showWindow(Any?)
Displays the window associated with the receiver.

var isWindowLoaded: Bool
A Boolean value that indicates whether the nib file containing the receiver’s window has been loaded.

var window: NSWindow?
The window owned by the receiver.

func windowDidLoad()
Sent after the window owned by the receiver has been loaded.

func windowWillLoad()
Sent before the window owned by the receiver is loaded.

### 访问`文档`

var document: AnyObject?
The document associated with the window controller.

func setDocumentEdited(Bool)
Sets the document edited flag for the window controller.

### 关闭`窗口`

func close()
Closes the window if it was loaded.

var shouldCloseDocument: Bool
A Boolean value that indicates whether the receiver necessarily closes the associated document when the window it manages is closed.

### 获取`Nib`和`Storyboard`的信息

var owner: AnyObject?
The owner of the nib file containing the window managed by the receiver.

var storyboard: NSStoryboard?
The storyboard file from which the window controller was loaded.

var windowNibName: NSNib.Name?
The name of the nib file that stores the window associated with the receiver.

var windowNibPath: String?
The full path of the nib file that stores the window associated with the receiver.

### 访问`窗口`属性和内容

var shouldCascadeWindows: Bool
A Boolean value that indicates whether the window will cascade in relation to other document windows when it is displayed.

var windowFrameAutosaveName: NSWindow.FrameAutosaveName
The name under which the frame rectangle of the window owned by the receiver is stored in the defaults database.

func synchronizeWindowTitleWithDocumentName()
Synchronizes the displayed window title and the represented filename with the information in the associated document.

func windowTitle(forDocumentDisplayName: String) -> String
Returns the window title to be used for a given document display name.

var contentViewController: NSViewController?
The view controller for the window’s content view.

* [func dismissController(Any?)](./1531963-dismisscontroller.md)

    关闭`窗口控制器`。

### 初始化

