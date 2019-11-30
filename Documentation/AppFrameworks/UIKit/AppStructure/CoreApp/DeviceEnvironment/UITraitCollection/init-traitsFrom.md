# init(traitsFrom:)

通过指定一个trait collections数组来返回一个新的由traits组成的trait collection。

## 声明

```swift
init(traitsFrom traitCollections: [UITraitCollection])
```

## 参数

* **traitCollections**

    [UITraitCollection](../)对象组成的数组。

## 返回值

返回一个新的由给定的trait collections数组里面的traits组成的trait collection。

## 说明

该方法需要一个或多个trait collection组成的数组，并将它们合并以创建一个新的trait collection。 如果数组包含多个元素，则将包含相同trait的最大索引值的元素用于该trait。 例如，下面的代码片断创建一个`compact`水平尺寸类的trait集合，因为数组中的第二个元素对应的值会覆盖第一个元素对应的值：

```swift
UITraitCollection *newHorizontalSizeClass1 = [UITraitCollection traitCollectionWithHorizontalSizeClass: UIUserInterfaceSizeClassRegular];
UITraitCollection *newHorizontalSizeClass2 = [UITraitCollection traitCollectionWithHorizontalSizeClass: UIUserInterfaceSizeClassCompact];
NSArray *traitArray = [NSArray arrayWithObjects: newHorizontalSizeClass1, newHorizontalSizeClass2, nil];
UITraitCollection *combinedTraits = [UITraitCollection traitCollectionWithTraitsFromCollections: traitArray];
```

## 其他内容

### 创建一个Trait Collection

#### [init()](../init.md)

返回一个新的所有属性被设置为默认（`unspecified`）值的trait collection。

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
