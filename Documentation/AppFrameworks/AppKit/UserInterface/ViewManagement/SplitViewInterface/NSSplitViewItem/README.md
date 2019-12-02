# NSSplitViewItem

`Split View Controller`中的一个`Item`。

## 定义

```swift
class NSSplitViewItem : NSObject
```

## 主题

### 创建一个`Split View Item`

* [init(contentListWithViewController: NSViewController)]()
* [init(sidebarWithViewController: NSViewController)]()
* [init(viewController: NSViewController)]()

### 管理`Split View Item`的厚度

* [var automaticMaximumThickness: CGFloat]()
* [var preferredThicknessFraction: CGFloat]()
* [var minimumThickness: CGFloat]()
* [var maximumThickness: CGFloat]()

### 获取`Auto Layout`行为

* [var holdingPriority: NSLayoutConstraint.Priority]()
* [class let unspecifiedDimension: CGFloat]()

### 获取`Split View Item`的行为

* [var behavior: NSSplitViewItem.Behavior]()
* [enum NSSplitViewItem.Behavior]()
* [var canCollapse: Bool]()
* [var isCollapsed: Bool]()
* [var collapseBehavior: NSSplitViewItem.CollapseBehavior]()
* [enum NSSplitViewItem.CollapseBehavior]()
* [var isSpringLoaded: Bool]()

### 获取`View Controller`

* [var viewController: NSViewController]()