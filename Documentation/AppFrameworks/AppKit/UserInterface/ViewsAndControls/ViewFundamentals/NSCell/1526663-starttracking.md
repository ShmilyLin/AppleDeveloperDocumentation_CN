# startTracking(at:in:)

开始跟踪接收者中的鼠标事件。

## 定义

```swift
func startTracking(at startPoint: NSPoint, 
                  in controlView: NSView) -> Bool
```

## 参数

* **startPoint**

    光标的初始位置。

* **controlView**

    管理接收者的`NSControl`对象。

## 返回值

如果将接收者设置为连续响应，或者在拖动鼠标时设置为响应，则为`true`；否则为`false`。

## 说明

跟踪开始时，[trackMouse(with:in:of:untilMouseUp:)](./1533606-trackmouse.md)的`NSCell`实现会调用此方法。子类可以重写此方法，以在鼠标跟踪开始时实现特殊的鼠标跟踪行为，例如，显示特殊的光标。