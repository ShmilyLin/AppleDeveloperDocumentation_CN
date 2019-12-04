# NSPanel

一种特殊类型的`窗口`，通常执行`辅助窗口`的功能。

## 定义

```swift
class NSPanel : NSWindow
```

## 概述

有关`面板`如何工作的详细信息（尤其是要了解其行为与`窗口`行为的区别），请参阅[`面板`如何工作](../../../../../../../DocumentationArchive/WindowProgrammingGuide/HowPanelsWork.md)。

## 主题

### 配置`面板`

* [var isFloatingPanel: Bool]()

一个布尔值，指示接收方是否为`浮动面板`。

* [var becomesKeyOnlyIfNeeded: Bool]()

一个布尔值，指示接收者是否仅在需要时才成为`Key窗口`。

* [var worksWhenModal: Bool]()

一个布尔值，指示即使模态运行其他某个`窗口`，`面板`是否也接收键盘和鼠标事件。

### 常量

* [Alert`面板`返回值]()

当模态会话使用由[NSGetAlertPanel]()函数提供的`NSPanel`运行模式会话时，这些常量定义由[NSRunAlertPanel]()函数和`NSApplication`方法[runModalSession(_:)]()返回的值。

* [模态`面板`返回值]()

这些常量定义了诸如[NSOpenPanel]()类的`runModal`...方法之类的方法的可能返回值，该方法指示用户在打开的`面板`上单击了哪个`按钮`（确定或取消）。

* [Style Masks]()

指定`面板`样式的常数。