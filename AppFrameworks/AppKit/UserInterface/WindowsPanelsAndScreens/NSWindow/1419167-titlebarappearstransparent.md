# titlebarAppearsTransparent

一个布尔值，指示标题栏是否绘制其背景。

## 定义

```swift
var titlebarAppearsTransparent: Bool { get set }
```

## 说明

当此属性的值为`true`时，标题栏不会绘制其背景，这将允许其下方的所有内容都显示出来。此属性设置为`true`后，只有当还设置了[NSFullSizeContentViewViewWindowMask]()时，才生效。
