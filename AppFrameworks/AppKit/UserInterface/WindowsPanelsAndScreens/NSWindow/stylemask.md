# NSWindow.StyleMask

这些常量指定窗口的样式，并且可以使用C位或运算符进行组合。

## 定义

```swift
struct StyleMask
```

## 主题

### 常量

* **static var borderless: NSWindow.StyleMask**

    该窗口不显示任何通常的外围元素。仅用于显示或缓存目的。除非[canBecomeKey]()或[canBecomeMain]()的值为`true`，否则使用`NSWindowStyleMaskBorderless`的窗口不能成为键或主窗口。请注意，你可以通过在“属性”检查器的“外观”部分中取消选择“标题栏”，在`Interface Builder`中将窗口或面板的样式蒙版设置为`NSWindowStyleMaskBorderless`。

* **static var titled: NSWindow.StyleMask**

    窗口显示一个标题栏。

* **static var closable: NSWindow.StyleMask**

    窗口显示一个关闭按钮。

* **static var miniaturizable: NSWindow.StyleMask**

    窗口显示一个最小化按钮。

* **static var resizable: NSWindow.StyleMask**

    窗口允许大小调整。

* **static var unifiedTitleAndToolbar: NSWindow.StyleMask**

    该常量无效，因为所有包含工具栏的窗口都使用统一样式。

* **static var fullScreen: NSWindow.StyleMask**

    窗口可以全屏显示。全屏窗口不会绘制其标题栏，并且可能对其工具栏进行特殊处理。（在调用[toggleFullScreen(_ :)]()时会自动切换这个值。）

* **static var fullSizeContentView: NSWindow.StyleMask**

    设置后，窗口的[contentView]()会占用整个窗口的大小。尽管你可以将此常量与其他窗口样式蒙版结合使用，但只有带有标题栏的窗口才可以使用该常量。请注意，对layer-backing使用此样式选项。使用[contentLayoutRect]()或[contentLayoutGuide]()在标题栏-工具栏区域下方布置视图。

* **static var utilityWindow: NSWindow.StyleMask**

    窗口是一个面板或是[NSPanel]()的一个子类。

* **static var docModalWindow: NSWindow.StyleMask**

    窗口是一个文档面板（或是[NSPanel]()的一个子类。）

* **static var nonactivatingPanel: NSWindow.StyleMask**

    窗口是一个不会激活所属应用程序的面板或[NSPanel]()的一个子类。

* **static var hudWindow: NSWindow.StyleMask**

    窗口是一个HUD面板。

### 初始化

* [init(rawValue: UInt)]()