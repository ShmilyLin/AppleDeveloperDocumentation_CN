# cellSize(forBounds:)

返回显示接收器所需的最小尺寸，并将其限制为指定的矩形。

## 定义

```swift
func cellSize(forBounds rect: NSRect) -> NSSize
```

## 参数

* **aRect**

    `Cell`的大小，或者如果`Cell`不是文本或图像`Cell`，则是`aRect`参数的大小。 如果该`Cell`是`Image Cell`，但未设置任何图像，则返回`NSSize.zero`。

## 说明

此方法考虑到由`Cell`的边框类型确定的特定偏移量内的图像或文本的大小。如果接收者是文本类型的，则调整文本的大小以适合`aRect`的大小（与`aRect`一样在`Cell`的边界之内）。

为了支持基于约束的布局，当自定义`Cell`的内容以这种方法的返回值发生更改的方式更改时，该`Cell`需要通过调用`Control`的[invalidateIntrinsicContentSize(for:)]()方法来通知其`Control`更改。