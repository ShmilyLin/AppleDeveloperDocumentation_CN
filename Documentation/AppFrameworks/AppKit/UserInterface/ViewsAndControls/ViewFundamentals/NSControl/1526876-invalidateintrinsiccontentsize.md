# invalidateIntrinsicContentSize(for:)

通知控件其`Cell`的固有内容大小不再有效。

## 定义

```swift
func invalidateIntrinsicContentSize(for cell: NSCell)
```

## 参数

* **cell**

    内部内容大小已更改的`Cell`。

## 说明

`Control`根据`Cell`返回的给定范围的`Cell`大小确定其固有内容大小。当`Cell`的内容以改变[cellSize(forBounds:)]()的返回值的方式更改时，`Cell`需要调用此方法来通知其控件其固有大小不再有效。