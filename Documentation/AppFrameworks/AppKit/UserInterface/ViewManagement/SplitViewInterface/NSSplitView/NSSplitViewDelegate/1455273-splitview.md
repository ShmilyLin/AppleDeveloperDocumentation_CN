# splitView(_:resizeSubviewsWithOldSize:)

允许`Delegate`为`NSSplitView`发送器的`子视图`指定自定义大小行为。

## 定义

```swift
optional func splitView(_ splitView: NSSplitView, 
  resizeSubviewsWithOldSize oldSize: NSSize)
```

## 参数

* **splitView**

    发送消息的`分隔视图`。

* **oldSize**

    用户调整大小之前，`分隔视图`的大小。

## 说明

如果`Delegate`实现此方法，则在调整`分隔视图`的大小之后，将调用[splitView(_:resizeSubviewsWithOldSize:)]()。

应该调整`子视图`的大小，以使`子视图`的大小之和加上分隔线的厚度之和等于`NSSplitView`新框架的大小。你可以通过[dividerThickness]()方法获得分隔线的厚度。

请注意，如果你实现此`Delegate`方法自己调整`子视图`的大小，则`NSSplitView`不会为你执行任何错误检查。但是，你可以调用[adjustSubviews()]()来执行默认的大小调整行为。