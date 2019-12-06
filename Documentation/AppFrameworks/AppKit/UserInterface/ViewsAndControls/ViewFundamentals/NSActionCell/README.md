# NSActionCell

`Control`内的一个活动区域。

## 定义

```swift
class NSActionCell : NSCell
```

## 概述

`NSActionCell`做三件事：显示文本或图标；提供其`NSControl`对象使用的`Target`对象和`Action`方法；通过适当高亮显示其区域并根据光标移动向其`Target`发送`Action`消息来处理鼠标（光标）跟踪。

## 主题

### 分配`Target`和`Action`

* [var action: Selector?](./1531427-action.md)

    返回接收器的`Action-Message`选择器。

* [var target: AnyObject?](./1535837-target.md)

    返回接收器的`Target`对象。

### 分配标签

* [var tag: Int](./1535314-tag.md)

    返回接收器的标签。