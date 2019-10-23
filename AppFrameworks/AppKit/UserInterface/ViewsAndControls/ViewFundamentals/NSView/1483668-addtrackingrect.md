# addTrackingRect(_:owner:userData:assumeInside:)

在视图中建立一个用于跟踪鼠标输入和鼠标退出事件的区域，并返回一个标识跟踪矩形的标签。

## 定义

```swift
func addTrackingRect(_ rect: NSRect, 
                      owner: Any, 
              userData data: UnsafeMutableRawPointer?, 
          assumeInside flag: Bool) -> NSView.TrackingRectTag
```

## 参数

* **aRect**

    定义视图区域的矩形，用于跟踪鼠标输入和鼠标退出的事件。

* **owner**

    发送事件消息的对象。只要它同时响应[mouseEntered(with:)]()和[mouseExited(with:)]()，它就可以是视图本身或其他对象（例如[NSCursor]()或自定义绘图工具对象）。

* **userData**

    每个跟踪事件在[NSEvent]()对象中存储的数据。

* **flag**

    如果为`true`，则在光标离开`aRect`时将生成第一个事件，无论添加跟踪矩形时光标是否在`aRect`内。 如果为`false`，则当光标最初位于`aRect`内时，如果光标离开`aRect`，或者如果光标最初位于`aRect`之外，则当光标进入`aRect`时，将生成第一个事件。你通常会希望将此标志设置为`false`。

## 返回值

标识跟踪矩形的标签。它存储在关联的[NSEvent]()对象中，可用于删除跟踪矩形。

## 说明

跟踪矩形提供了一种通用机制，可用于根据光标位置触发动作（例如，状态栏或提示字段，可提供有关光标位于其上的项目的信息）。要简单地在特定区域上更改光标，请使用[addCursorRect(_:cursor:)]()。如果必须使用跟踪矩形来更改光标，则[NSCursor]()类规范描述了必须使用跟踪矩形来调用以更改光标的其他方法。

在`macOS 10.5`及更高版本中，跟踪区域提供了更大范围的功能（请参阅[addTrackingArea(_:)]()）。