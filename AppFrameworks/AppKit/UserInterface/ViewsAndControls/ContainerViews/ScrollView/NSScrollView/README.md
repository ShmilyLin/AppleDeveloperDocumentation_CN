# NSScrollView

显示文档视图的一部分并提供滚动条的视图，允许用户在滚动视图内移动文档视图。

## 定义

```swift
class NSScrollView : NSView
```

## 概述

`NSScrollView`类是`AppKit`滚动设备的中央协调器，该类由该类以及[NSClipView]()和[NSScroller]()类组成。

在滚动视图（常规配置）中使用[NSClipView]()对象时，应直接向滚动视图发出控制背景绘图状态的消息，而不是向剪辑视图发送消息。

## 主题

### 计算布局

### 确定组件尺寸

### 管理图形属性

### 管理视图

* [var contentView: NSClipView](./1403547-contentview.md)

    滚动视图的内容视图，即剪切文档视图的视图。

* [var documentView: NSView?](./1403485-documentview.md)

    滚动视图的视图在其内容视图中滚动。

* [func addFloatingSubview(NSView, for: NSEvent.GestureAxis)]()

    将浮动子视图添加到文档视图。

### 管理滚动

### 管理标尺

### 管理缩进

### 滚动条样式

* [var scrollerKnobStyle: NSScroller.KnobStyle](./1403544-scrollerknobstyle.md)

    使用覆盖滚动条样式的滚动视图的旋钮样式。

* [var scrollerStyle: NSScroller.Style](./1403520-scrollerstyle.md)

    滚动视图使用的滚动样式。

### 设置滚动行为

### 滚动后更新显示

### 排列组件

### 查找栏位置

### 指定文档的主要滚动行为

### 指定滚动视图弹性

### 闪烁的滚动条

### 缩放滚动视图

### 常量

### 通知

### 初始化