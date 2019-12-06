# trackMouse(with:in:of:untilMouseUp:)

启动`Cell`中的鼠标跟踪行为。

## 定义

```swift
func trackMouse(with event: NSEvent, 
              in cellFrame: NSRect, 
            of controlView: NSView, 
         untilMouseUp flag: Bool) -> Bool
```

## 参数

* **theEvent**

    导致鼠标跟踪发生的事件。

* **cellFrame**

    接收者的框架矩形。

* **controlView**

    包含接收者的`视图`。通常这是一个`NSControl`对象。

* **untilMouseUp**

    如果为`true`，则继续进行鼠标跟踪，直到用户释放鼠标按键为止。如果为`false`，则无论鼠标按键处于什么状态，跟踪都会继续进行，直到光标离开由`cellFrame`参数指定的跟踪矩形为止。有关更多信息，请参见`说明`。

## 返回值

如果满足鼠标跟踪条件，则为`true`，否则为`false`。

## 说明

通常不会覆盖此方法，因为这个方法的默认实现会调用其他的`NSCell`的方法，这些方法可以被覆盖以处理拖动会话中的特定事件。此方法的返回值取决于`untilMouseUp`标志。如果`untilMouseUp`设置为`true`，则当光标位于任意位置时，如果鼠标按键向上移动，则此方法返回`true`；否则为`false`。如果`untilMouseUp`设置为`false`，则当光标在`cellFrame`内时鼠标按键向上移动时，此方法返回`true`；否则为`false`。

此方法首先调用[startTracking(at:in:)](./1526663-starttracking.md)，如果该方法返回`true`，则在侦听鼠标拖动的事件时，将调用[continueTracking(last:current:in:)]()，直到该方法返回`false`或释放鼠标为止。最后，如果释放鼠标，将调用[stopTracking(last:current:in:mouseIsUp:)]()。如果`untilMouseUp`为`true`，则当光标在任意位置时，当鼠标按键向上移动时会调用它。如果`untilMouseUp`为`false`，则当光标位于`cellFrame`内时，当鼠标按键向上移动时会调用它。通常，你将覆盖这些方法中的一种或多种以响应特定的鼠标事件。

