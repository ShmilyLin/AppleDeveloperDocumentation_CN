# Legacy Customizations

直接在Tab Bar Item对象上自定义外观信息。

## 概述

在iOS 13及更高版本中，使用[standardAppearance]()属性自定义Tab Bar Item。你也可以继续使用这些旧式访问器直接覆盖Tab Bar Item的外观。

## 主题

### 配置标题

* [var titlePositionAdjustment: UIOffset]()

    用于调整标题位置的偏移量。

### 配置选中状态的图片

* [var selectedImage: UIImage?]()

    Tab Bar Item选中状态显示的图像。

### 配置Badge

* [var badgeValue: String?]()

    在Item的右上角显示的带有红色椭圆形的文本。

* [var badgeColor: UIColor?]()

    应用于Badge的背景色。

* [func setBadgeTextAttributes([NSAttributedString.Key : Any]?, for: UIControl.State)]()

    指定Badge文本的自定义文本属性。

* [func badgeTextAttributes(for: UIControl.State) -> [NSAttributedString.Key : Any]?]()

    检索与Item的Badge文本关联的自定义文本属性。