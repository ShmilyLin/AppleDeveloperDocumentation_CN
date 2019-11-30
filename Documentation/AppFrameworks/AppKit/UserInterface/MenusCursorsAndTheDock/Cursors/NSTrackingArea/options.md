# NSTrackingArea.Options

为[init(rect:options:owner:userInfo:)]()的`options`参数中指定的常量定义的数据类型。这些常量如下所述；你可以通过对它们执行按位或运算来指定多个常量。特别是，你必须提供一个或多个跟踪类型常量（即[mouseEnteredAndExited]()，[mouseMoved和cursorUpdate]()）和一个活动常量（即[activeWhenFirstResponder]()，[activeInKeyWindow]()，[activeInActiveApp]()和[activeAlways]()）。另外，你可以指定任何行为常量（即，假设为[inside]()，[inVisibleRect]()和[enabledDuringMouseDrag]()）。

## 定义

```swift
struct Options
```

## 主题

### 常量

* **static var mouseEnteredAndExited: NSTrackingArea.Options**

    当鼠标光标进入该区域时，跟踪区域的所有者将收到[mouseEntered(with:)]()；当鼠标离开该区域时，[mouseExited(with:)]()事件将被接收。此值指定跟踪区域的类型。

* **static var mouseMoved: NSTrackingArea.Options**

    当鼠标光标位于跟踪区域内时，跟踪区域的所有者会收到[mouseMoved(with:)]()消息。此值指定跟踪区域的类型。

* **static var cursorUpdate: NSTrackingArea.Options**

    当鼠标光标进入跟踪区域时，跟踪区域的所有者会收到[cursorUpdate(with:)]()消息；当鼠标离开该区域时，光标将被适当地重置。此值指定跟踪区域的类型。

* **static var activeWhenFirstResponder: NSTrackingArea.Options**

    当视图是第一响应者时，所有者将收到消息。此值指定何时激活[NSTrackingArea]()对象定义的跟踪区域。

* **static var activeInKeyWindow: NSTrackingArea.Options**

    当视图在Key窗口中时，所有者将收到消息。此值指定何时激活[NSTrackingArea]()对象定义的跟踪区域。

* **static var activeInActiveApp: NSTrackingArea.Options**

    当应用程序处于活动状态时，所有者将收到消息。此值指定何时激活[NSTrackingArea]()对象定义的跟踪区域。

* **static var activeAlways: NSTrackingArea.Options**

    所有者接收消息，而不管响应者状态，窗口状态或应用程序状态如何。与该常数一起指定[cursorUpdate]()选项时，不会发送[cursorUpdate(with:)]()消息。此值指定何时激活[NSTrackingArea]()对象定义的跟踪区域。

* **static var assumeInside: NSTrackingArea.Options**

    当光标离开跟踪区域时，无论将[NSTrackingArea]()添加到视图中，光标是否位于该区域内，都会生成第一个事件。如果未指定此选项，则当光标最初位于该区域内时，如果光标离开跟踪区域，或者如果光标最初位于该区域外，则进入该区域时，将生成第一个事件。通常，您不应该指定此行为。此值指定由[NSTrackingArea]()定义跟踪区域的行为。

* **static var inVisibleRect: NSTrackingArea.Options**

    鼠标跟踪仅发生在视图的可见矩形中，也就是说，跟踪矩形的未被遮挡的区域。否则，无论重叠的视图如何，整个跟踪区域都是活动的。[NSTrackingArea]()对象会自动与视图的可见区域（visibleRect）中的更改同步，并且将从rect返回的值忽略。此值指定由[NSTrackingArea]()定义的跟踪区域的行为。

* **static var enabledDuringMouseDrag: NSTrackingArea.Options**

    当将鼠标光标拖到跟踪区域中时，所有者将收到[NSMouseEntered]()事件。 如果未指定此选项，则在将鼠标移动到跟踪区域中（没有按下按钮）时，所有者会在鼠标拖动后收到[NSerftMouseUp]()事件，并接收鼠标输入的事件。