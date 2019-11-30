# appearance

AppKit用于绘制应用程序界面的外观。

## 定义

```swift
var appearance: NSAppearance? { get set }
```

## 说明

当此属性的值为`nil`（默认值）时，AppKit会将当前系统外观应用于应用程序的用户界面元素，包括其窗口，视图，面板和弹出窗口。将[NSAppearance]()对象分配给此属性会导致应用的界面元素改为采用指定的外观。

各个窗口和视图可能仍会覆盖应用的外观，以自定义其外观。