# NSWindow.BackingStoreType

这些常量指定窗口设备如何在窗口中完成绘制。

## 定义

```swift
enum BackingStoreType : UInt
```

## 主题

### 常量

* **case buffered**

    该窗口将所有图形渲染到显示缓冲区中，然后将其刷新到屏幕上。

    说明：
        你应该使用此模式。它支持硬件加速，Quartz绘图，并在可能的情况下利用GPU。它还使用合成器支持Alpha通道绘制，不透明度控件。