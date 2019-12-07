# mouseDownFlags

最后一个鼠标按下（左键）事件的修饰符标志。

## 定义

```swift
var mouseDownFlags: Int { get }
```

## 说明

此属性的值是来自最新[NSEvent]()对象的修饰符标志的值，代表鼠标按下事件。如果尚未发生跟踪，或者事件不包含修饰键，则此属性的值为`0`。