# UIModalPresentationStyle

呈现View Controller时可用的模态呈现样式。

## 定义

```swift
enum UIModalPresentationStyle : Int
```

## 主题

### 呈现

* [case automatic](./automatic.md)

    系统选择的默认呈现样式。

* [case none](./none.md)

    一种呈现样式，表示不应进行任何修改。

* [case fullScreen](./fullscreen.md)

    一种呈现样式，其中所呈现的View覆盖整个屏幕。

* [case pageSheet](./pagesheet.md)

    一种呈现样式，部分覆盖了基础内容。

* [case formSheet]()

    一种呈现样式，用于在屏幕中央显示内容。

* [case currentContext]()

    一种呈现样式，其中内容显示在另一个View Controller的内容上。

* [case custom]()

    一种自定义View呈现样式，由一种自定义呈现Controller和一个或多个自定义动画对象管理。

* [case overFullScreen]()

    View呈现样式，其中所呈现的View覆盖屏幕。

* [case overCurrentContext]()

    一种呈现样式，其中内容显示在另一个View Controller的内容上。

* [case popover]()

    一种呈现样式，其中内容以弹出View显示。

* [case blurOverFullScreen]()

    在全屏呈现中显示新内容之前，使基础内容模糊的呈现样式。
