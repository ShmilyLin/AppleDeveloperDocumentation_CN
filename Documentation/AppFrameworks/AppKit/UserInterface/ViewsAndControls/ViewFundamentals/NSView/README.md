# NSView

用于在应用程序中绘制，打印和处理事件的基础结构。

## 定义

```swift
class NSView : NSResponder
```

## 概述

通常，你不应该直接使用`NSView`对象。相反，你应该使用继承自`NSView`的对象，或者你自己对`NSView`进行子类化，并覆盖其方法以实现所需的行为。`NSView`类（或其子类之一）的实例通常称为视图对象，或简称为视图。

视图可处理你应用的可见内容的图像与交互。你可以在一个[NSWindow]()对象中安放一个或多个视图，该对象充当内容的包装。视图对象定义了一个矩形区域，用于绘制和接收鼠标事件。视图还可以处理其他琐事，包括拖动图标以及使用[NSScrollView]()类来支持有效的滚动。

`NSView`类的大多数功能都是由`AppKit`自动调用的。除非你要实现`NSView`的具体子类或在运行时密切配合视图层次结构的内容，否则你无需对此类界面的了解太多。对于任何视图，你可以按原样使用许多方法。通常使用以下方法。

* [frame]()返回`NSView`对象的位置和大小。

* [bounds]()返回`NSView`对象的内部原点和大小。

* [needsDisplay]()确定是否需要重绘`NSView`对象。

* [window]()返回包含`NSView`对象的[NSWindow]()对象。

* [draw(_:)]()绘制`NSView`对象。（所有子类都必须实现此方法，但是很少显式调用它。）

有关`NSView`实例如何处理事件和操作消息的更多信息，请参见[Cocoa事件处理指南]()。有关显示工具提示和上下文菜单的更多信息，请参见[显示上下文菜单]()和[管理工具提示]()。

### 子类化提示

当涉及子类化和继承时，`NSView`可能是`AppKit`中最重要的类。你在Cocoa应用程序中看到的大多数用户界面对象都是从`NSView`继承的对象。如果要创建以特殊方式绘制自身的对象，或者以特殊方式响应鼠标单击的对象，则可以创建`NSView`的自定义子类（或从`NSView`继承的类）。子类化NSView是一个常见且重要的过程，一些技术文档描述了如何绘制自定义子类以及如何响应自定义子类中的事件。请参阅[Cocoa绘图指南]()和[Cocoa事件处理指南]()（尤其是“[处理鼠标事件]()”和“[鼠标事件]()”）。

### 在你的子类里处理事件

如果直接子类化`NSView`并处理特定类型的事件，则与事件相关的方法的实现通常不应调用`super`。视图从其[NSResponder]()父类继承其事件处理功能。响应者的默认行为是将事件沿响应者链传递，如果你在自定义视图中处理事件，这通常不是你想要的行为。因此，如果你的视图实现以下任何方法并处理事件，则不应调用`super`：

* [mouseDown(with:)]()
* [mouseDragged(with:)]()
* [mouseUp(with:)]()
* [mouseMoved(with:)]()
* [mouseEntered(with:)]()
* [mouseExited(with:)]()
* [rightMouseDragged(with:)]()
* [rightMouseUp(with:)]()
* [otherMouseDown(with:)]()
* [otherMouseDragged(with:)]()
* [otherMouseUp(with:)]()
* [scrollWheel(with:)]()
* [keyDown(with:)]()
* [keyUp(with:)]()
* [flagsChanged(with:)]()
* [tabletPoint(with:)]()
* [tabletProximity(with:)]()

> 注意：
> 
> 由于`NSView`更改了[rightMouseDown:]()方法的默认行为，因此在自定义子类中实现该方法时应调用`super`。

如果你的视图来自`NSView`以外的其他类，请调用super来让父视图处理你不执行的任何事件。

## 主题

### 创建实例

### 管理视图层次结构

### 修改框架矩形

### 修改内容边界矩形

### 管理视图的Layer

### 管理与Layer相关的属性

### 绘制

### 打印

### 分页

### 使视图的内容无效

### 转换坐标值

### 修改坐标系

### 检查坐标系修改

### 调整子视图的大小

### 使用布局锚点创建约束

### 管理视图的约束

### 使用布局指南

### 自动布局中的测量

### 将视图与自动布局对齐

### 触发自动布局

### 选择加入自动版式

### 调试自动布局

### 聚焦

### 聚焦环绕绘制

### Getting the Vibrancy Setting

### 全屏模式

### 隐藏视图

### 管理实时调整大小

### 管理手势识别器

### 事件处理

### 触摸事件处理

### Key视图循环管理

### 滚动

### 拖动操作

### 处理智能放大

### 控制通知

### 响应后备存储属性中的更改

### 按标签搜索

### 工具提示

### 管理跟踪矩形

* [func addTrackingRect(NSRect, owner: Any, userData: UnsafeMutableRawPointer?, assumeInside: Bool) -> NSView.TrackingRectTag](./1483668-addtrackingrect.md)

    在视图中建立一个用于跟踪鼠标输入和鼠标退出事件的区域，并返回一个标识跟踪矩形的标签。

* [func removeTrackingRect(NSView.TrackingRectTag)]()

    根据标签删除对的跟踪矩形。

### 管理跟踪区域

* [func addTrackingArea(NSTrackingArea)](./1483489-addtrackingarea.md)

    将给定的跟踪区域添加到视图中。

* [func removeTrackingArea(NSTrackingArea)]()

    从视图中删除给定的跟踪区域。

* [var trackingAreas: [NSTrackingArea]]()

    视图跟踪区域的数组。

* [func updateTrackingAreas()]()

    当视图的几何形状发生更改，从而需要重新计算其跟踪区域时，会自动调用。

### 管理光标跟踪

* [func addCursorRect(NSRect, cursor: NSCursor)]()

    建立当鼠标指针位于指定区域内时要使用的光标。

* [func removeCursorRect(NSRect, cursor: NSCursor)]()

    从视图中完全删除光标矩形。

* [func discardCursorRects()]()

    使所有使用`addCursorRect(_：cursor:)`设置的光标矩形无效。

* [func resetCursorRects()]()

    子类重写以定义其默认光标矩形。

### 管理上下文菜单

### 编写符合标准的渲染说明

### 显示定义窗口

### 绘制查找指示器

### 管理内容布局方向

### 指定OpenGL表面分辨率

### 配置压力

### 常量

### 通知

### 初始化

### 实例属性

### 类属性

### 实例方法

### 枚举