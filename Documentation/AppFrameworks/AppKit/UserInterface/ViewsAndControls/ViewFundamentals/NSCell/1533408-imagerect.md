# imageRect(forBounds:)

返回接收方在其中绘制其图像的矩形。

## 定义

```swift
func imageRect(forBounds rect: NSRect) -> NSRect
```

## 参数

* **theRect**

    接收者的边界矩形。

## 返回值

接收者在其中绘制图像的矩形。此矩形与`theRect`中的矩形略有偏移。