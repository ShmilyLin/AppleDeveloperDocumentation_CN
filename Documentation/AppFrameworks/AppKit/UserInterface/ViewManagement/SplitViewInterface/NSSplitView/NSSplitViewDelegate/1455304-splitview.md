# splitView(_:canCollapseSubview:)

允许`Delegate`确定用户是否可以折叠和取消折叠`子视图`。

## 定义

```swift
optional func splitView(_ splitView: NSSplitView, 
         canCollapseSubview subview: NSView) -> Bool
```

## 参数

* **splitView**

    发送消息的`分隔视图`。

* **subview**

    将要折叠的`子视图`。

## 返回值

如果`子视图`在用户将分隔线拖动到其最小尺寸和边缘之间的中途标记之外时应合拢，则为`true`，否则为`false`。

## 说明

当用户将分隔线向后拖动到其最小尺寸和其边缘之间的中途标记处时，`子视图`不会折叠。

要指定最小大小，请定义方法[splitView(_:constrainMaxCoordinate:ofSubviewAt:)]()和[splitView(_:constrainMinCoordinate:ofSubviewAt:)]()。仅当你还定义[splitView(_:constrainMinCoordinate:ofSubviewAt:)]()时，`子视图`才能折叠。

折叠后的`子视图`被隐藏，但由`分隔视图`对象保留，其大小与折叠前的大小相同。

如果`Delegate`未实现此方法，则`子视图`无法折叠。