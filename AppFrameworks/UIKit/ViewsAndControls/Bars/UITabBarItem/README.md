# UITabBarItem

Tab Bar的一项。

## 定义

```swift
class UITabBarItem : UIBarItem
```

## 概述

Tab Bar在单选模式下运行，在该模式下一次只能选择一个选项——点击Tab Bar Item可切换Tab Bar上的显示。你还可以在Tab Bar Item上指定badge以添加其他视觉信息，例如，消息类应用程序使用该Item上的badge来显示新消息的数量。此外，该类还提供了许多系统默认值的Item。

使用[init(tabBarSystemItem:tag:)]()方法创建系统的Item。使用[init(title:image:tag:)]()方法创建具有指定标题和图像的自定义Item，该Item将同时拥有用选中和未选中的图像。使用[init(title:image:selectedImage:)]()方法创建具有指定标题、未选中图像和选中图像的自定义Item。

### 自定义外观

iOS 5.0及更高版本中，你可以使用[UIBarItem]()声明的外观选择器来设置Item的标签文本属性，从而自定义Tab Bar的外观。你也可以使用[自定义Item外观]()中列出的方法。你可以使用外观代理（例如`[UITabBarItem appearance]`）或仅单个Tab Bar Item来自定义所有Tab Bar Item的外观。

默认情况下，未选中和选中的图像是根据源图像中的alpha值自动创建的。如果不希望系统自动变色，请为图像提供[UIImage.RenderingMode.alwaysOriginal]()。

有关外观和行为配置的更多信息，请参见[Tab Bars]()。

## 主题

### 初始化

* [init(tabBarSystemItem: UITabBarItem.SystemItem, tag: Int)]()

    创建并返回一个包含指定系统Item的新Tab Bar Item。

* [init(title: String?, image: UIImage?, tag: Int)]()

    使用指定的属性创建并返回一个新Tab Bar Item。

* [init(title: String?, image: UIImage?, selectedImage: UIImage?)]()

    创建并返回具有指定标题，未选中的图像和选中的图像的新Tab Bar Item。

* [init()]()

    将Tab Bar Item初始化为默认状态。

* [init?(coder: NSCoder)]()

* [enum UITabBarItem.SystemItem]()

    可以在Tab Bar上使用的系统项目。

### 自定义Item的外观

* [var standardAppearance: UITabBarAppearance?]()

    当前Tab Bar Item的外观设置。

* [Legacy Customizations](./LegacyCustomizations/)

    直接在Tab Bar Item对象上自定义外观信息。