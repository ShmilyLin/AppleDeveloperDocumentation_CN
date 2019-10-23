# NSWindowController

管理窗口的控制器，通常是存储在nib文件中的窗口。

## 定义

```swift
class NSWindowController : NSResponder
```

## 概述

管理窗口需要以下：

* 加载并显示窗口
* 在适当的时候关闭窗口
* 自定义窗口标题
* 将窗口的框架（大小和位置）存储在默认数据库中
* 将窗口与应用程序的其他文档窗口相关联

窗口控制器可以自己管理窗口，也可以作为AppKit基于文档的体系结构中的角色扮演者来管理窗口，该体系结构还包括[NSDocument]()和[NSDocumentController]()对象。在这种体系结构中，窗口控制器由“document”（NSDocument子类的实例）创建和管理，并依次保留对文档的引用。

窗口控制器和nib文件之间的关系很重要。尽管窗口控制器可以管理以编程方式创建的窗口，但是通常它会在nib文件中管理窗口。nib文件可以包含其他顶级对象，包括其他窗口，但是窗口控制器的责任是该主窗口。窗口控制器通常是nib文件的所有者，即使它是基于文档的应用程序的一部分也是如此。无论文件的所有者是谁，窗口控制器都负责释放加载的nib文件中的所有顶级对象。

对于简单的文档（即，只有一个包含窗口的nib文件的文档），你不需要使用`NSWindowController`进行任何操作，AppKit会为你创建一个。但是，如果默认的窗口控制器不足，则可以创建[NSWindowController]()的自定义子类。对于具有多个窗口或面板的文档，你的文档必须创建[NSWindowController]()（或[NSWindowController]()的自定义子类）的单独实例，每个窗口或面板一个。一个示例CAD应用程序具有不同的窗口，分别用于绘制对象的侧视图，俯视图和正视图。您在[NSDocument]()子类中的操作确定使用默认的[NSWindowController]()还是单独创建和配置的[NSWindowController]()对象。

### 子类化NSWindowController

当你想增加默认行为时，应该创建`NSWindowController`的子类，例如为窗口赋予自定义标题或在加载窗口之前执行一些设置任务。在你的子类的初始化方法中，请确保在用super调用`initWithWindowNibName:...`初始化程序或[init(window :)]()初始化程序。选择的初始化程序取决于window对象是源自nib文件还是以编程方式创建。

你还可以实现`NSWindowController`子类，以避免在实例化窗口控制器时要求客户端代码获取相应的nib文件名并将其传递给[init(windowNibName:)]()或[init(windowNibName:owner:)]()。最好的方法是重写windowNibName以返回nib的文件名，并通过将nil传递给[init(window:)]()来实例化窗口控制器。使用[init(window:)]()指定的初始值设定项可简化对Swift初始值设定项的要求。

通常，你需要重写表1中列出的方法之一。

| 方法名 | 说明 |
|:---|:---|
| [windowWillLoad()]() | 在加载nib文件之前执行一些任务 |
| [windowDidLoad()]() | 在加载nib文件之后执行一些任务 |
| [windowTitle(forDocumentDisplayName:)] | 自定义窗口标题 |

你也可以重写[loadWindow()]()以获得不同的nib查询或nib加载行为，尽管通常无需这样做。