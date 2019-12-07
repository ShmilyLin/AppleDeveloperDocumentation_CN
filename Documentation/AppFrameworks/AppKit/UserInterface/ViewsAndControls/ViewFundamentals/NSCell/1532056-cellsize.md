# cellSize

显示`Cell`所需的最小尺寸。

## 定义

```swift
var cellSize: NSSize { get }
```

## 说明

此属性包含绘制其内容所需的最小`Cell`大小（以点为单位）。如果该`Cell`不是文本或图像`Cell`，则`Cell`大小设置为`(10000, 10000)`。如果`Image Cell`尚未关联图像，则`Cell`大小为[NSSize.zero]()。此方法考虑了`Cell`中图像或文本的大小以及`Cell`边框所需的任何边距区域（如果有）。
