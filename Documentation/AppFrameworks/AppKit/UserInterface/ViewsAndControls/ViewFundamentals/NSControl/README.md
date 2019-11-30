# NSControl

控件的基本行为的定义，这些控件是专门的视图，可通过使用目标动作设计模式将相关事件通知给你的应用。

## 定义

```swift
class NSControl : NSView
```

## 概述

`NSControl`类是抽象的，必须被子类化才能使用。尽管你可以自己对它进行子类化，但更推荐的是，你应该使用`AppKit`已经定义的子类。控件在屏幕上绘制内容，自动处理与该内容的用户交互，并针对任何重要的用户交互调用其目标对象的[action]()方法。

### 关于协议方法

`NSControl`类为其子类提供了几种协议方法，这些方法允许进行文本编辑，例如[NSTextField]()和[NSMatrix]()。其中包括：[controlTextDidBeginEditing(_:)]()，[controlTextDidChange(_:)]()和[controlTextDidEndEditing(_:)]()。

请注意，尽管`NSControl`定义了协议方法，但它本身没有协议。使用这些方法的任何子类都必须具有一个协议以及获取和设置它的方法。此外，正式的协议[NSControlTextEditingDelegate]()还定义了控件协议使用的协议方法。