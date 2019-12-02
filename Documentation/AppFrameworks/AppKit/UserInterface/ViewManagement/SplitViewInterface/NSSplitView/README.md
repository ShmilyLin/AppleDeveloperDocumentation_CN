# NSSplitView

在水平或垂直运行的线性堆栈中排列两个或多个`View`的`View`。

## 定义

```swift
class NSSplitView : NSView
```

## 概述

`Split View`管理`Split View Controller`（[NSSplitViewController]()类的实例）的分隔线和方向。默认情况下`Split View Controller`中，分隔线是水平方向的，因此包含的同级`View`从上到下垂直排列。

分隔线索引从零开始，最左边或最顶部的分隔线（取决于[isVertical]()属性的值）的索引为0。

## 主题

### 自定义`Split View`行为

* [var delegate: NSSplitViewDelegate?]()

`Split View`的`Delegate`。

* [protocol NSSplitViewDelegate]()

`NSSplitViewDelegate`协议定义[NSSplitView]的`Delegate`可选实现的方法。

### 管理`Split View Item`

* [class NSSplitViewItem]()

`Split View Controller`中的一个`Item`。

### 安排`Subview`

* [var arrangedSubviews: [NSView]]()
* [var arrangesAllSubviews: Bool]()
* [func addArrangedSubview(NSView)]()
* [func insertArrangedSubview(NSView, at: Int)]()
* [func removeArrangedSubview(NSView)]()

### 管理`Subview`

* [func adjustSubviews()]()

调整`Split View`的`Subview`的大小，以便它们（加上分隔线）填充`Split View`。

* [func isSubviewCollapsed(NSView) -> Bool]()

返回指定的`View`是否折叠。

* [func holdingPriorityForSubview(at: Int) -> NSLayoutConstraint.Priority]()

调整大小时，返回`Subview`的宽度或高度的优先级。

* [func setHoldingPriority(NSLayoutConstraint.Priority, forSubviewAt: Int)]()

设置`Split View`的`Subview`保持其宽度或高度的优先级。

### 管理分隔线方向

* [var isVertical: Bool]()

`Split View`的分隔线的几何方向，如果为`true`，则是垂直分隔线和并排视图的样式。

### 配置和绘制分隔线

* [var dividerStyle: NSSplitView.DividerStyle]()

`View`之间绘制的分隔线样式。

* [var dividerColor: NSColor]()

`Split View`在`Subview`之间绘制的分隔线的颜色。

* [var dividerThickness: CGFloat]()

`Split View`的分隔线的厚度。

* [func drawDivider(in: NSRect)]()

在接收者的两个`Subview`之间绘制分隔线。

### 保存`Subview`的位置

* [var autosaveName: NSSplitView.AutosaveName?]()

自动保存`Split View`的分隔符配置的名称。

* [typealias NSSplitView.AutosaveName]()

### 限制分隔位置

* [func minPossiblePositionOfDivider(at: Int) -> CGFloat]()

返回分隔符在指定索引处的最小可能位置。

* [func maxPossiblePositionOfDivider(at: Int) -> CGFloat]()

返回分隔符在指定索引处的最大可能位置。

* [func setPosition(CGFloat, ofDividerAt: Int)]()

设置分隔线在指定索引处的位置。

### 常量

* [enum NSSplitView.DividerStyle]()

这些常量指定[NSSplitView]()可以使用的分隔符样式。

### 通知

`NSSplitView`声明并发布以下通知。此外，它还发布由其`Superclass`——`NSView`声明的通知。有关更多信息，请参见[NSView]()类规范。

* [class let didResizeSubviewsNotification: NSNotification.Name]()

在`NSSplitView`更改其部分或全部`Subview`的大小后发布。

* [class let willResizeSubviewsNotification: NSNotification.Name]()

在`NSSplitView`更改其部分或全部`Subview`的大小前发布。