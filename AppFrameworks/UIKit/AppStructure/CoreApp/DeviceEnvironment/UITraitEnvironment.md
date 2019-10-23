# UITraitEnvironment Protocol

使你的应用可使用iOS接口环境的一组方法。

## 概述

iOS接口环境包括诸如横向和纵向尺寸、显示比例和用户界面习惯用法等。要访问遵守此协议的对象的trait环境，请使用`traitCollection`属性。该协议还提供了一种当接口环境发生变化时被系统调用的可覆盖方法。实现此方法作为创建自适应iOS应用程序的一部分。

有关trait collection的更多信息，请参阅[UITraitCollection](https://developer.apple.com/documentation/uikit/uitraitcollection)。有关在iOS中创建自适应界面的WWDC 2014演示文稿，请参阅[使用UIKit构建自适应应用程序](https://developer.apple.com/videos/wwdc/2014/#216)。

## 专题

### 一、访问Trait Collection

#### var traitCollection: UITraitCollection

一个View Controller（[UIViewController](https://developer.apple.com/documentation/uikit/uiviewcontroller)类或其子类的实例）或一个View（[UIView](https://developer.apple.com/documentation/uikit/uiview)类或其子类的实例）的trait collection。

##### 声明

```swift
var traitCollection: UITraitCollection { get }
```

##### 说明

view controllers和views都遵守`UITraitEnvironment`协议。

> **重要**
> 
> 直接使用`traitCollection`属性。 不要重写它。 不要提供自定义实现。

### 二、响应接口环境的变化

#### func traitCollectionDidChange(UITraitCollection?)

iOS接口环境发生变化时调用。

##### 声明

```swift
func traitCollectionDidChange(_ previousTraitCollection: UITraitCollection?)
```

##### 参数

* **previousTraitCollection**
  
  接口环境改变之前的[UITraitCollection](https://developer.apple.com/documentation/uikit/uitraitcollection)对象。

##### 说明

当iOS接口环境发生变化时，系统会调用此方法。根据你的应用程序的需求，在view controller和view中实现此方法，以响应此类更改。例如，当iPhone从纵向旋转到横向时，你可以调整view controller下子视图的布局。此方法的默认实现为空。

在实现的开始阶段，请调用super以确保视图层次结构中较高的界面元素有机会首先调整其布局。使用上与下面代码类似：

```swift
- (void) traitCollectionDidChange: (UITraitCollection *) previousTraitCollection {
    [super traitCollectionDidChange: previousTraitCollection];
    if ((self.traitCollection.verticalSizeClass != previousTraitCollection.verticalSizeClass)
        || (self.traitCollection.horizontalSizeClass != previousTraitCollection.horizontalSizeClass)) {
        // your custom implementation here
    }
}
```

## 相关

### 继承自

[NSObjectProtocol](https://developer.apple.com/documentation/objectivec/nsobjectprotocol)

### 被遵守

* [UIPresentationController](https://developer.apple.com/documentation/uikit/uipresentationcontroller)
* [UIScreen](https://developer.apple.com/documentation/uikit/uiscreen)
* [UIView](https://developer.apple.com/documentation/uikit/uiview)
* [UIViewController](https://developer.apple.com/documentation/uikit/uiviewcontroller)

## 其他内容

### 设备环境

#### [Responding to Changing Display Modes on Apple TV](https://developer.apple.com/documentation/uikit/core_app/responding_to_changing_display_modes_on_apple_tv)

当设备上的屏幕色域发生变化时，动态更改图像和资源。

#### [class UIDevice](https://developer.apple.com/documentation/uikit/uidevice)

表示当前设备。

#### [class UITraitCollection](./UITraitCollection.md)

通过trait定义你的应用的iOS接口环境，例如横向和纵向尺寸，显示比例和用户界面惯用语等。

#### [protocol UIAdaptivePresentationControllerDelegate](https://developer.apple.com/documentation/uikit/uiadaptivepresentationcontrollerdelegate)

一组与图像控制器一起确定如何响应应用程序中trait变化的方法。