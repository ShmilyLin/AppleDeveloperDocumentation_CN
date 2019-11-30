# scrollerStyle

滚动视图使用的滚动样式。

## 定义

```swift
var scrollerStyle: NSScroller.Style { get set }
```

## 说明

请参见[NSScroller.Style]()以获取可能的值。

此设置是在运行时根据用户的首选项设置以及（如果相关）连接的指向设备的集合及其配置的滚动功能（由[NSScroller]()的[preferredScrollerStyle]()确定）自动设置的。

设置滚动视图的滚动条样式可以设置水平和垂直滚动条的样式。如果滚动视图随后创建或分配了新的水平或垂直滚动器，则会为它们分配与分配给滚动视图相同的滚动器样式。