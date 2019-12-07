# AppKit

为你的macOS App构建并管理一个图形化的、事件驱动型的用户界面。

## 概述

AppKit包含一个macOS应用中所有你需要实现的用户界面的对象——`窗口（Window）`、`面板（Panel）`、`菜单（Menu）`、`滚动条（Scroller）`和`文本字段（Text Fields）`——并且它会为你处理所有高效的绘制到屏幕上所需要的细节、与硬件设备和屏幕缓存之间的沟通、绘制之前的屏幕区域清理、以及剪切视图。

这个框架也提供了让残疾人用户能够很容易使用你的App的接口（详见[无障碍](https://developer.apple.com/documentation/appkit/accessibility)）；想要学习更多关于为不同语言、国家、文化区域本地化你的App，请查看[国际化和本地化指南](https://developer.apple.com/library/content/documentation/MacOSX/Conceptual/BPInternational/Introduction/Introduction.html#//apple_ref/doc/uid/10000171i)。

## 专题

### 一、应用结构

* [App核心](./CoreApp/)

学习关于你用来和系统交互的对象。

* [文档、文件和iCloud]

使用文档管理应用程序的数据，并将其存储到本地文件系统或iCloud中。

* [Cocoa Bindings](./CocoaBindings/)

使用Cocoa Bindings自动将数据模型与应用程序界面同步。

* [资源管理]()

管理包含了你应用的用户界面的`storyboards`和`nib`文件，并学习如何加载存储在资源文件中的数据。



### 二、用户界面

你应用的用户界面提供视觉、听觉和触觉反馈给用户来告知你的应用在做什么。

* [在你的界面中支持深色模式](./SupportingDarkModeInYourInterface/)

除标准亮度外观外，还采用深色外观。

* [Supporting Continuity Camera in Your Mac App]()

使用`Continuity Camera`将使用用户的iPhone，iPad或iPod touch拍摄的扫描文档和图片合并到Mac应用程序中。

* [`视图(View)`和`控制器(Control)`](./UserInterface/ViewsAndControls/)

在屏幕上显示你的内容并定义这些内容的交互。

* [`视图(View)`管理](./UserInterface/ViewManagement/)

管理你的用户界面，包括视图(View)窗口(Window)中的大小和位置。

* [`菜单（Menu）`、`光标（Cursor）`和`Dock`）]()

实现菜单和光标与你的应用进行交互，并且用你应用的Dock图标传递最新的信息。

* [`窗口（Window）`、`面板（Panel）`、和`屏幕（Screen）`]()

组织你的视图的层次结构，以便于它们在屏幕上显示。

* [Touch Bar]()

在Touch Bar中显示交互内容和控件。

* [`动画（Animation）`]()

让你的视图和其他内容动起来，来给用户创造一个更具吸引力的体验。

* [`声音（Sound）`、`语音（Speech）`、和`触觉（Haptics）`]()

将播放声音和触觉反馈、以及语音识别和合成集成到你的界面中。



### 四、用户交互

* [`鼠标（Mouse）`、`键盘（Keyboard）`、和`触控板（Trackpad）`]()

处理关于鼠标、键盘和触控板输入的事件。

* [`手势（Gestures）`]()

在手势识别器中封装你应用的事件处理逻辑，这样你就可以在你整个应用的代码中重用。

* [`拖动（Drag）`和`放下（Drop）`]()

让你应用的内容支持使用拖放直接进行操作。

* [`无障碍（Accessibility）`]()

使你的应用更容易的让残疾人用户使用。


### 五、图形、绘制、颜色和打印

* [图形（Images）和PDF]()

创建并管理位图、PDF以及其他格式的图片。

* [绘制（Drawing）]()

在屏幕上绘制形状、图片以及其他内容。

* [颜色（Color）]()

使用内置或自定义格式表示颜色，并且为用户提供选项来选择并显示颜色。

* [打印（Printing）]()

显示系统打印面板并管理打印过程。



### 六、文本

* [文字显示]()

显示文字和检查拼写。

* [TextKit]()

管理文本存储并在app的视图中执行基于文本的内容的自定义布局。

* [字体（Fonts）]()

管理用于显示文本的字体。

### 七、快速操作

通过“快速操作”，你的应用程序扩展程序可以显示在“Finder预览”窗格、“快速操作”菜单和“触摸栏”中。

* [Add Functionality to Finder with Action Extensions]()
Implement Action Extensions to provide quick access to commonly used features of your app.

* [property list key NSExtensionServiceAllowsFinderPreviewItem]()
A Boolean value indicating whether the extension appears in the Finder Preview pane and Quick Actions menu.

* [property list key NSExtensionServiceFinderPreviewLabel]()
A name for display when the extension appears in the Finder Preview pane and Quick Actions menu.

* [property list key NSExtensionServiceFinderPreviewIconName]()
The name of an icon for display when the extension appears in the Finder Preview pane and Quick Actions menu.

* [property list key NSExtensionServiceAllowsTouchBarItem]()
A Boolean value indicating whether the extension appears as a Quick Action in the Touch Bar.

* [property list key NSExtensionServiceTouchBarLabel]()
A name for display when the extension appears as a Quick Action in the Touch Bar.

* [property list key NSExtensionServiceTouchBarIconName]()
The name of an icon for display when the extension appears as a Quick Action in the Touch Bar

* [property list key NSExtensionServiceTouchBarBezelColorName]()
The color to use for the bezel around the extension when it appears as a Quick Action in the Touch Bar.


### 八、被废弃的

* [弃用的符号](https://developer.apple.com/documentation/appkit/deprecated_symbols)


### 九、结构体

* [struct NSAccessibility]()
* [struct NSDiffableDataSourceSnapshot]()
Beta

### 十、类

* [class NSBindingSelectionMarker]()
* [class NSButtonTouchBarItem]()
* [class NSCollectionViewCompositionalLayout]()
* [class NSCollectionViewCompositionalLayoutConfiguration]()
* [class NSCollectionViewDiffableDataSource]()
Beta
* [class NSCollectionViewDiffableDataSourceReference]()
* [class NSColorSampler]()
* [class NSMenuToolbarItem]()
* [class NSPickerTouchBarItem]()
* [class NSSharingServicePickerToolbarItem]()
* [class NSStepperTouchBarItem]()
* [class NSTextCheckingController]()


### 十一、协议

* [protocol NSSharingServicePickerToolbarItemDelegate]()
* [protocol NSTextCheckingClient]()
* [protocol NSTextInputTraits]()
* [protocol NSUserActivityRestoring]()


### 十二、参考

* [Enumerations]()
Enumerations for use with multiple classes.

* [Functions]()

Functions and function-like macros for use with multiple classes.

* [Data Types]()

Data types for use with multiple classes.

---
## 其他内容