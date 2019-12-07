# stopTracking(last:current:in:mouseIsUp:)

停止接收者中的鼠标跟踪事件。

## 定义

```swift
func stopTracking(last lastPoint: NSPoint, 
               current stopPoint: NSPoint, 
                  in controlView: NSView, 
                  mouseIsUp flag: Bool)
```

## 参数

* **lastPoint**

    光标的上一个位置。

* **stopPoint**

    光标的当前位置

* **controlView**

    管理接收者的`NSControl`对象。

* **flag**

    如果为`true`，则因为用户释放了鼠标按键而调用此方法。否则，如果为`false`，即光标离开指定的跟踪矩形。

## 说明

当光标离开接收者的边界或鼠标按键向上移动时，[trackMouse(with:in:of:untilMouseUp:)](./1533606-trackmouse.md)的默认`NSCell`实现将调用此方法。此方法的默认`NSCell`实现不执行任何操作。子类通常会重写此方法以提供自定义的跟踪行为。下面的示例在单击鼠标按键时增加拥有三种状态的`Cell`的状态：

```swift
- (void)stopTracking:(NSPoint)lastPoint at:(NSPoint)stopPoint
    inView:(NSView *)controlView mouseIsUp:(BOOL)flag
{
    if (flag == YES) {
        [self setTriState:([self triState]+1)];
    }
}
```