# titleRect(forBounds:)

返回接收方在其中绘制其图像的矩形。

## 定义

```swift
func titleRect(forBounds rect: NSRect) -> NSRect
```

## 参数

* **theRect**

    接收者的边界矩形。

## 返回值

接收者在其中绘制文本的矩形。

## 说明

如果接收方是文本类型的`Cell`，则此方法将向内调整标题（`theRect`）的绘图矩形的大小，以使其具有较小的偏移量以容纳`Cell`边框。如果接收方不是文本类型的`Cell`，则该方法不执行任何操作。
