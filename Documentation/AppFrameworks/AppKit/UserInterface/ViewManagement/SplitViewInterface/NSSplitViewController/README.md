# NSSplitViewController

一个对象，该对象管理相邻`Subview`的数组，并具有用于管理这些`View`之间的分隔线的`Split View`对象。

## 定义

```swift
class NSSplitViewController : NSViewController
```

## 概述

`Split View Controller`的完整对象体系结构要复杂一些。具体来说，一个`Split View Controller`拥有一个`Split View Item`组成的数组（[NSSplitViewItem]()类型），每个`Split View Item`都具有一个`View Controller`（[NSViewController]()类型）和对应的`View`。`Subview`和`分隔符`都包含在`Split View Controller`自己的`View`中。

`Split View Controller`作为其`Split View`对象（管理分隔符的对象）的`Delegate`。如果重写`Split View Delegate`方法，则你的重写必须调用`super`。

默认情况下，`Subview`在`Split View Controller`的`View`中从上到下垂直排列。要指定水平（并排）排列，请实现`Split View Controller`的[splitView]()对象的`vertical`属性以返回`true`（返回`true`将指定垂直分隔线，并因此指定水平视图排列）。

若要使用`Split View Controller`，必须对`Subview`使用`Auto Layout`，并支持折叠和显示`Subview`的动画。例如，如果你设计的布局包含两个`View`，一个内容区域和一个可选的侧栏，则可以使用`Auto Layout`约束来指定在侧栏可见时内容区域是缩小还是保持相同的大小。

`Split View Controller`对其`View`进行延迟加载。例如，将折叠的`Split View Item`添加为新的子项直到它被显示时才加载相关`View`。

有关在你的App中使用`NSSplitViewController`的更多信息，请参见[使用`Outline View`和`Split View`导航分层数据](../../../../CoCoaBindings/navigating_hierarchical_data_using_outline_and_split_views.md)。

## 主题

### 配置和管理`Split View Controller`

* [var splitView: NSSplitView]()

由`Split View Controller`管理的`Split View`。

* [func splitViewItem(for: NSViewController) -> NSSplitViewItem?]()

根据给定的`Child View Controller`返回`Split View Controller`中的相应`Split View Item`。

* [var splitViewItems: [NSSplitViewItem]]()

与`Split View Controller`的`Child View Controller`相对应的`Split View Item`的数组。

### 修改`Split View Controller`

* [func addSplitViewItem(NSSplitViewItem)]()

将`Split View Item`添加到`Split View Controller`的`splitViewItems`数组的末尾。

* [func insertSplitViewItem(NSSplitViewItem, at: Int)]()

将`Split View Item`添加到`Split View Controller`的`splitViewItems`数组中的指定索引位置。

* [func removeSplitViewItem(NSSplitViewItem)]()

从`Split View Controller`中删除指定的`Split View Item`。

### 实例属性

* [var minimumThicknessForInlineSidebars: CGFloat]()

### 类型属性

* [class let automaticDimension: CGFloat]()

### 实例方法

* [func splitView(NSSplitView, additionalEffectiveRectOfDividerAt: Int) -> NSRect]()
* [func splitView(NSSplitView, canCollapseSubview: NSView) -> Bool]()
* [func splitView(NSSplitView, effectiveRect: NSRect, forDrawnRect: NSRect, ofDividerAt: Int) -> NSRect]()
* [func splitView(NSSplitView, shouldHideDividerAt: Int) -> Bool]()
* [func toggleSidebar(Any?)]()
* [func validateUserInterfaceItem(NSValidatedUserInterfaceItem) -> Bool]()
* [func viewDidLoad()]()