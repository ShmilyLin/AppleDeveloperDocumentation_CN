# calcDrawInfo(_:)

重新计算`Cell`的几何形状。

## 定义

```swift
func calcDrawInfo(_ rect: NSRect)
```

## 参数

* **aRect**

    计算`Cell`信息时要使用的参考矩形。

## 说明

管理`NSCell`对象的对象（例如控件）通常会维护一个标志，该标志会通知它们是否已修改了它们的任意一个`Cell`，从而应重新计算`Cell`的位置或大小。如果是这样，则在显示`Cell`之前会自动调用`NSControl`的[calcSize()]()方法，并且该方法将调用`Cell`的`calcDrawInfo(_:)`方法。

此方法的默认实现不执行任何操作。
