# UITraitCollection

通过trait定义你的应用的iOS接口环境，例如横向和纵向尺寸，显示比例和用户界面风格等。

## 概述

iOS trait环境通过[UITraitEnvironment](https://juejin.im/post/5abc5a306fb9a028e12005d2)协议的`traitCollection`属性公开。该协议被以下类所遵守：[UIScreen]()，[UIWindow]()，[UIViewController]()，[UIPresentationController]()和[UIView]()。要创建自适应界面，请根据这些trait的变化来编写代码以调整你的应用的布局。你可以使用`UITraitCollection`的`horizontalSizeClass`，`verticalSizeClass`，`displayScale`和`userInterfaceIdiom`属性来访问对应的trait值。表达习惯用法和尺寸特征的值在[UIUserInterfaceIdiom]()和[UIUserInterfaceSizeClass]()枚举中定义，显示比例特征的值为浮点数。

要使view controller和view响应iOS接口环境中的更改，请重写[UITraitEnvironment](https://juejin.im/post/5abc5a306fb9a028e12005d2)中的`traitCollectionDidChange(_:)`方法。要响应接口环境更改来自定义view controller动画，请重写[UIContentContainer](https://developer.apple.com/documentation/uikit/uicontentcontainer)协议的`willTransition(to:with:)`方法。

图1显示了你的应用在各种设备上全屏运行时可能遇到的水平（宽度）和垂直（高度）尺寸类别。

![图1](https://docs-assets.developer.apple.com/published/f85dff2bbd/110734d0-900d-43e9-ac0f-d32bfa4fc30c.png)

有关你的应用在iPad上的“幻灯片放映”和“拆分视图”中遇到的大小的信息，请参阅[在iPad上采用多任务增强功能](https://developer.apple.com/library/content/documentation/WindowsViews/Conceptual/AdoptingMultitaskingOniPad/index.html#//apple_ref/doc/uid/TP40015145)中的[幻灯片放映和拆分视图快速入门](https://developer.apple.com/library/content/documentation/WindowsViews/Conceptual/AdoptingMultitaskingOniPad/QuickStartForSlideOverAndSplitView.html#//apple_ref/doc/uid/TP40015145-CH13)。

您可以创建独立trait collection以帮助匹配特定环境。`UITraitCollection`类包含四个专门的构造函数以及一个系统构造函数，它可以让你组合一系列trait collection，`init(traitsFrom:)`。

独立trait collection的一个重要用途是启用基于当前iOS接口环境的图像的额外用处。你可以通过[UIImageAsset](https://developer.apple.com/documentation/uikit/uiimageasset)实例将一个trait collection与[UIImage](https://developer.apple.com/documentation/uikit/uiimage)实例相关联，如[UIImageAsset](https://developer.apple.com/documentation/uikit/uiimageasset)的概述部分所述。有关在Xcode IDE中以图形方式配置Asset目录的信息，请参阅[Asset目录帮助]()。

你可以使用一个独立trait collection在iPhone上以横向方式启用两列分割视图。请参阅[UIViewController]()类的`setOverrideTraitCollection(_:forChildViewController:)`方法。

如[UIAppearance](https://developer.apple.com/documentation/uikit/uiappearance)中所述，独立trait collection也被用于通过`appearance(for:) `协议方法定制视图外观。

### 3D Touch和Trait Collections

从iOS 9开始，你可以使用该类来检查你的应用程序所运行的设备是否支持3D Touch：读取应用的trait环境中任何对象的trait collection上的`forceTouchCapability`属性的值。有关trait环境的信息，请参阅[UITraitEnvironment](https://juejin.im/post/5abc5a306fb9a028e12005d2)。有关`forceTouchCapability`属性的可能值，请参阅[UIForceTouchCapability](https://developer.apple.com/documentation/uikit/uiforcetouchcapability)枚举。

由于用户可以在设置中关闭3D Touch，请在实现`traitCollectionDidChange(_:)`方法时检查`forceTouchCapability`属性的值，然后根据属性的值调整代码。

## 专题

### 一、创建一个Trait Collection

#### [init()](./init.md)

返回一个新的所有属性被设置为默认（`unspecified`）值的trait collection。

#### [init(traitsFrom: \[UITraitCollection\])](./init-traitsFrom.md)

通过指定一个trait collections数组来返回一个新的由traits组成的trait collection。

#### [init(userInterfaceIdiom: UIUserInterfaceIdiom)]()

返回一个新的只包含一个指定的界面风格的trait collection。

#### [init(horizontalSizeClass: UIUserInterfaceSizeClass)]()

返回一个新的只包含一个指定的水平尺寸类别的trait collection。

#### [init(verticalSizeClass: UIUserInterfaceSizeClass)]()

返回一个新的只包含一个指定的垂直尺寸类别的trait collection。

#### [init(forceTouchCapability: UIForceTouchCapability)]()

创建一个只包含一个3D Touch是否可用的trait collection。

#### [init(displayScale: CGFloat)]()

返回一个新的只包含一个指定的显示比例的trait collection。

#### [init(displayGamut: UIDisplayGamut)]()

返回一个新的只包含一个指定的显示色域特征的trait collection。

#### [init(layoutDirection: UITraitEnvironmentLayoutDirection)]()

返回一个新的只包含一个指定的布局方向特征的trait collection。

#### [init(preferredContentSizeCategory: UIContentSizeCategory)]()

返回一个新的只包含一个指定的内容尺寸特征的trait collection。

#### [init(userInterfaceStyle: UIUserInterfaceStyle)]()

返回一个新的只包含一个指定的用户界面样式特征的trait collection。

#### [init?(coder: NSCoder)]()

### 二、查询尺寸类别Traits

#### [var horizontalSizeClass: UIUserInterfaceSizeClass]()

trait collection的水平尺寸类别。

#### [var verticalSizeClass: UIUserInterfaceSizeClass]()

trait collection的垂直尺寸类别。

#### [enum UIUserInterfaceSizeClass]()

定义一个view的尺寸类别。

### 三、查询与显示相关的Traits

#### [var displayScale: CGFloat]()

trait collection的显示比例。

#### [var displayGamut: UIDisplayGamut]()

当前显示的色域。

#### [enum UIDisplayGamut]()

指示当前显示色域的常数。

### 四、查询界面相关的Traits

#### [var userInterfaceIdiom: UIUserInterfaceIdiom]()

trait collection的用户界面风格。

#### [enum UIUserInterfaceIdiom]()

应该在当前设备上使用的界面类型。

#### [var forceTouchCapability: UIForceTouchCapability]()

trait collection的3D Touch可用性。

#### [enum UIForceTouchCapability]()

指示设备上3D Touch可用性的key。只有某些设备支持3D Touch。在那些支持的设备上，用户可以在“设置”的“辅助功能”区域中禁用3D Touch。

#### [var layoutDirection: UITraitEnvironmentLayoutDirection]()

与当前环境关联的布局方向。

#### [enum UITraitEnvironmentLayoutDirection]()

指示与当前环境关联的布局方向的常量。

#### [var userInterfaceStyle: UIUserInterfaceStyle]()

与用户界面相关的样式。

#### [enum UIUserInterfaceStyle]()

指示应用程序界面样式的常量。

### 五、检索内容大小类别信息

#### [var preferredContentSizeCategory: UIContentSizeCategory]()

用户可能比较喜欢的字体大小。

#### [struct UIContentSizeCategory]()

指示你的内容大小的常量。

### 六、比较Trait Collections

#### [func containsTraits(in: UITraitCollection?)]()

返回一个布尔值，该值表示该trait collection是否包含其他trait collection中含有的所有值。

## 相关

### 继承自

[NSObject](https://developer.apple.com/documentation/objectivec/nsobject)

### 遵守

* [CVarArg](https://developer.apple.com/documentation/swift/cvararg)
* [Equatable](https://developer.apple.com/documentation/swift/equatable)
* [Hashable](https://developer.apple.com/documentation/swift/hashable)
* [NSCopying](https://developer.apple.com/documentation/foundation/nscopying)
* [NSSecureCoding](https://developer.apple.com/documentation/foundation/nssecurecoding)

## 其他内容

### 设备环境

#### [Responding to Changing Display Modes on Apple TV](https://developer.apple.com/documentation/uikit/core_app/responding_to_changing_display_modes_on_apple_tv)

当设备上的屏幕色域发生变化时，动态更改图像和资源。

#### [class UIDevice](https://developer.apple.com/documentation/uikit/uidevice)

表示当前设备。

#### [protocol UITraitEnvironment](https://juejin.im/post/5abc5a306fb9a028e12005d2)

使你的应用可使用iOS接口环境的一组方法。

#### [protocol UIAdaptivePresentationControllerDelegate](https://developer.apple.com/documentation/uikit/uiadaptivepresentationcontrollerdelegate)

一组与图像控制器一起确定如何响应应用程序中trait变化的方法。