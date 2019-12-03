# NSSegmentedControl

在一个水平组中显示一个或多个按钮。

## 定义

```swift
class NSSegmentedControl : NSControl
```

## 概述

`NSSegmentedControl`类使用[NSSegmentedCell]()类来实现控件的许多功能。`NSSegmentedControl`中的大多数方法只是覆盖方法，它们会调用`NSSegmentedCell`中的相应方法。没有覆盖的`NSSegmentedCell`方法与访问和设置标签和工具提示的值、以编程方式设置键段以及建立控件的模式有关。

`分段控件`的功能包括：

* `段`可以具有图像，文本（`Label`），菜单，工具提示和`Tag`。

* `分段控件`可以包含图像或文本，但不能同时包含两者。

* 控件整体或单个`段`均可启用或禁用。

* `分段控件`具有四种跟踪模式，在[NSSegmentedControl.SwitchTracking]()中有所描述。你可以将这些模式与[trackingMode]()属性一起使用。

* 每个`段`可以是固定宽度，也可以是自动调整大小以适合内容。

* 如果`段`中有文本并标记为自动调整大小，则文本可能会被截断，以便控件完全适合。

* 如果图像太大而无法放入片段中，则会对其进行裁剪。

* 如果在`系统偏好设置`>`键盘`中启用了`完全键盘访问`，则可以使用键盘在各`段`之间移动并选择各`段`。