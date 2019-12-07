# continueTracking(last:current:in:)

返回一个布尔值，该值指示鼠标跟踪是否应在接收`Cell`中持续进行。

## 定义

```swift
func continueTracking(last lastPoint: NSPoint, 
              current currentPoint: NSPoint, 
                   in controlView: NSView) -> Bool
```

## 参数

* **lastPoint**

    包含开始跟踪时光标的初始位置或上一个`currentPoint`。

* **currentPoint**

    光标的当前位置

* **controlView**

    管理接收者的`NSControl`对象。

## 返回值

如果应该继续进行鼠标跟踪，则为`true`，否则为`false`。

## 说明

在[trackMouse(with:in:of:untilMouseUp:)](./1533606-trackmouse.md)中调用此方法。如果将`Cell`设置为在按下鼠按键或拖动鼠标时将动作消息连续发送到其目标，则默认实现返回`true`。子类可以重写此方法以提供更复杂的跟踪行为。

