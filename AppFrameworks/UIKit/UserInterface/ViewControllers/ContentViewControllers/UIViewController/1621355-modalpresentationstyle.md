# modalPresentationStyle

模态呈现View Controller时的呈现样式。

## 定义

```swift
var modalPresentationStyle: UIModalPresentationStyle { get set }
```

## 说明

呈现样式决定了模态呈现的View Controller如何在屏幕上显示。在水平紧凑（Horizontally Compact）的环境中，模态View Controller始终以全屏显示。在水平规则（Horizontally Regular）的环境中，有几种不同的呈现样式选项。

此属性的默认值为[UIModalPresentationStyle.automatic](./UIModalPresentationStyle/)。有关可能的呈现样式及其与可用过渡样式的兼容性的列表，请参见[UIModalPresentationStyle](./UIModalPresentationStyle/)常量说明。