# 视图(View)管理

管理你的用户界面，包括视图(View)窗口(Window)中的大小和位置。

## 主题

### 第一步

* [class NSViewController]()

A controller that manages a view, typically loaded from a nib file.

### `窗口`管理

* [class NSWindowController](./NSWindowController/)

管理`窗口`的`控制器`，通常是存储在`nib`文件中的一个`窗口`。

* [class NSTitlebarAccessoryViewController]()

An object that manages a custom view—known as an accessory view—in the title bar–toolbar area of a window. 

### 分页界面

* [class NSPageController]()
An object that controls swipe navigation and animations between views or view content.

### `Split View`界面

* [class NSSplitViewController](./SplitViewInterface/NSSplitViewController/)

一个对象，该对象管理相邻`Subview`的数组，并具有用于管理这些`View`之间的分隔线的`Split View`对象。

* [class NSSplitView](./SplitViewInterface/NSSplitView/)

在水平或垂直运行的线性堆栈中排列两个或多个`View`的`View`。

* [class NSSplitViewItem](./SplitViewInterface/NSSplitViewItem/)

`Split View Controller`中的一个`Item`。

### `Stack View`界面

* [class NSStackView]()
A view that arranges an array of views horizontally or vertically and that automatically updates their placement and sizing when the window size changes.

### `Tab View`界面

* [class NSTabViewController]()
A container view controller that manages a tab view interface, which organizes multiple pages of content but displays only one page at a time.

* [class NSTabView]()
A multipage interface that displays one page at a time.

class NSTabViewItem]()
An item in a tab view.

### 媒体库界面

* [class NSMediaLibraryBrowserController]()
An object that configures and displays a Media Library Browser panel.