# NSAppearance

管理应用程序中UI元素的标准外观属性的对象。

## 定义

```swift
class NSAppearance : NSObject
```

## 概述

`NSAppearance`对象管理`AppKit`如何呈现应用程序的UI元素。具体来说，Appearance对象确定在绘制Window，View和Control时`AppKit`使用哪些颜色和图像。尽管可以使用Appearance对象确定如何绘制自定义View和Control，但是更好的方法是选择自动适应当前外观的颜色和图像。例如，定义一种Color Asset，其实际颜色值会针对浅色和深色外观而变化。你可以在`Interface Builder`中为View分配特定外观。

用户选择系统的默认外观，但是你可以覆盖重新定义整个或部分应用程序的外观。应用程序继承默认的系统外观，Window继承其应用程序的外观，View继承其最近祖先的外观（Super View或Window）。要强制Window或View采用其他外观，请将特定的Appearance对象分配给其`appearance`属性。

`AppKit`绘制控件时，它将自动将当前线程上的当前外观设置为控件的外观。当前的外观会影响绘制路径并在你访问系统字体和颜色时返回你给定的值。当前外观还影响文本和图像的外观，例如工具栏中的文本和模板图像。


## 主题

### 创建外观

* [init?(named: NSAppearance.Name)]()

    根据标准系统外观之一的名称创建外观对象。

* [init?(appearanceNamed: NSAppearance.Name, bundle: Bundle?)]()

    从位于指定捆绑软件中的命名外观文件创建外观对象。

* [init?(coder: NSCoder)]()

### 获取外观名称


* [var name: NSAppearance.Name]()

    外观的名称。

* [struct NSAppearance.Name]()

### 确定最合适的外观

* [func bestMatch(from: [NSAppearance.Name]) -> NSAppearance.Name?]()

    返回与当前外观对象最匹配的外观名称。

### 获取并设置当前外观

* [class var current: NSAppearance!]()

    返回在当前线程上处于活动状态的外观对象。

### 管理震动

* [var allowsVibrancy: Bool]()

    指定当前外观是否允许振动。