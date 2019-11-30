# init()

返回一个新的所有属性被设置为默认（`unspecified`）值的trait collection。

## 定义

```swift
init()
```

## 返回值

一个所有traits被设置为“`unspecified`”的trait collection。

## 其他内容

### [init(traitsFrom: \[UITraitCollection\])](../init-traitsFrom.md)

通过指定一个trait collections数组来返回一个新的由traits组成的trait collection。

### [init(userInterfaceIdiom: UIUserInterfaceIdiom)]()

返回一个新的只包含一个指定的界面风格的trait collection。

### [init(horizontalSizeClass: UIUserInterfaceSizeClass)]()

返回一个新的只包含一个指定的水平尺寸类别的trait collection。

### [init(verticalSizeClass: UIUserInterfaceSizeClass)]()

返回一个新的只包含一个指定的垂直尺寸类别的trait collection。

### [init(forceTouchCapability: UIForceTouchCapability)]()

创建一个只包含一个3D Touch是否可用的trait collection。

### [init(displayScale: CGFloat)]()

返回一个新的只包含一个指定的显示比例的trait collection。

### [init(displayGamut: UIDisplayGamut)]()

返回一个新的只包含一个指定的显示色域特征的trait collection。

### [init(layoutDirection: UITraitEnvironmentLayoutDirection)]()

返回一个新的只包含一个指定的布局方向特征的trait collection。

### [init(preferredContentSizeCategory: UIContentSizeCategory)]()

返回一个新的只包含一个指定的内容尺寸特征的trait collection。

### [init(userInterfaceStyle: UIUserInterfaceStyle)]()

返回一个新的只包含一个指定的用户界面样式特征的trait collection。

### [init?(coder: NSCoder)]()