# Outline View Button Keys

`Outline View`用这些键创建展开和折叠`Items`的按钮。



## 概述

`Outline View`创建这些按钮通过调用它继承来的[`makeView(withIdentifier:owner:)`](https://developer.apple.com/documentation/appkit/nstableview/1535482-makeview)方法，传入键作为标识符，`delegate`作为所有者。



> Note
>
> 这些键向后兼容到OS X v10.7，然而，the symbol is not exported prior to v10.9 and the string value (`@"NSOutlineViewDisclosureButtonKey"`) must be used.



## 讲解

### 常量

#### class let disclosureButtonIdentifier: NSUserInterfaceItemIdentifier

常用的三角按钮。

###### 声明

```swift
class let disclosureButtonIdentifier: NSUserInterfaceItemIdentifier
```



#### class let showHideButtonIdentifier: NSUserInterfaceItemIdentifier

显示／隐藏按钮。

###### 声明

```swift
class let showHideButtonIdentifier: NSUserInterfaceItemIdentifier
```



