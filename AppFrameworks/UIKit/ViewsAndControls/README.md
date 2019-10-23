# Views和Controls

　　在屏幕上显示你的内容并定义该内容允许的交互。

---
## 概述

　　视图（view）和控件（control）是应用程序用户界面的可视构建块。使用它们在屏幕上绘制和整理应用的内容。

![用于创建提醒的屏幕包括标签（label），开关（switch）和许多其他类型的view。](https://docs-assets.developer.apple.com/published/4d53baf7cb/75c071dc-3a79-466b-99d1-f8ef216a94aa.png)

　　view可以托管其他view。将一个view嵌入另一个view中会在主视图（称为**superview**）和嵌入视图（称为**subview**）之间创建一个包含关系。查看层次结构可以更轻松地管理view。

　　你还可以使用view执行以下任何操作：

* 响应触摸（touch）和其他事件（直接处理或与手势识别器（gesture recognizer）协调）。

* 使用Core Graphics或UIKit类绘制自定义内容。

* 支持拖放（drag and drop）交互。

* 响应焦点（focus）变化。

* 为view的大小，位置和外观属性设置动画。

　　[UIView]()是所有视图的根类，并定义了它们的常见行为。[UIControl]()定义了特定于按钮（button）、开关（switch）和为用户交互设计的其他view的其他行为。

　　有关如何使用view和control的其他信息，请参阅[iOS人机界面指南](https://developer.apple.com/ios/human-interface-guidelines)。

---
## 专题

### 一、View基础知识

#### ● [class UIView]()

　　管理屏幕上矩形区域内容的对象。

### 二、容器视图（container view）

　　使用容器视图（container view）组织和显示大型数据集。

#### ● [Collection Views]()

　　使用可配置且高度可自定义的布局显示嵌套视图（view）。

#### ● [Table Views](./TableViews/)

　　在可自定义行的单列中显示数据。

#### ● [class UIStackView]()

　　简化的界面，用于在列或行中布置视图（view）集合。

#### ● [class UIScrollView]()

　　允许滚动和缩放其包含视图（view）的视图（view）。

### 三、内容视图（content view）

#### ● [class UIActivityIndicatorView]()

　　显示任务正在进行的视图（view）。

#### ● [class UIImageView]()

　　在界面中显示单个图像或一系列动画图像的对象。

#### ● [class UIPickerView]()

　　使用旋转轮或类似插槽机的东西来显示一组或多组值的视图（view）。

#### ● [class UIProgressView]()

　　描述任务随时间推移进度的视图（view）。

#### ● [~~class UIWebView~~]() 【已废弃】

　　在你的应用中嵌入网页内容的视图（view）。

### 四、控件（control）

　　收集输入并响应用户与控件（control）的交互。

#### ● [class UIControl]()

　　控件（control）的基类，它是为响应用户交互而传达特定操作或意图的可视元素。

#### ● [class UIButton]()

　　用于响应用户交互执行自定义代码的控件（control）。

#### ● [class UIDatePicker]()

　　用于输入日期和时间值的控件（control）。

#### ● [class UIPageControl]()

　　一个显示一系列水平点的控件（control），每个点对应于应用程序文档或其他数据模型实体中的页面。

#### ● [class UISegmentedControl]()

　　由多个段组成的水平控件（control），每个段都可以看作一个按钮。

#### ● [class UISlider]()

　　用于从连续值范围中选择一个值的控件（control）。

#### ● [class UIStepper]()

　　用于递增或递减值的控件（control）。

#### ● [class UISwitch]()

　　提供二进制选择的控件，例如`On/Off`。

### 五、文本视图（text view）

　　使用文本视图（text view）显示和编辑文本。

#### ● [class UILabel]()

　　显示一行或多行只读文本的视图，通常与控件（control）一起使用以描述其预期用途。

#### ● [class UITextField]()

　　在界面中显示可编辑文本区域的对象。

#### ● [class UITextView]()

　　可滚动的多行文本区域。

#### ● [拖放自定义]()

　　扩展对文本视图的标准拖放支持，以包括自定义类型的内容。

### 六、视觉效果

#### ● [class UIVisualEffect]()

　　用于视觉效果视图（visual effect view）以及模糊和震动效果对象的初始化程序。

#### ● [class UIVisualEffectView]()

　　实现一些复杂视觉效果的对象。

#### ● [class UIVibrancyEffect]()

　　放大并调整视觉效果视图（visual effect view）后面的内容颜色的对象。

#### ● [class UIBlurEffect]()

　　将模糊效果应用于视觉效果视图（visual effect view）后面的内容的对象。

### 七、Bars

　　管理导航栏（navigation bar）、选项卡栏（tab bar）、搜索栏（search bar）以及工具栏（tool bar）上面的items。

#### ● [class UIBarItem]()

　　可以添加到屏幕底部显示的栏中的item的抽象超类。

#### ● [class UIBarButtonItem]()

　　专门用于放置在工具栏（tool bar）或选项卡栏（tab bar）上的按钮。

#### ● [class UIBarButtonItemGroup]()

　　iPad上键盘上方快捷方式栏（shortcuts bar）上的一组条形按钮的item。

#### ● [class UINavigationBar]()

　　导航控件显示在屏幕顶部的栏中，通常与导航控制器（navigation controller）结合使用。

#### ● [class UISearchBar]()

　　用于从用户接收搜索相关信息的专用视图（view）。

#### ● [class UIToolbar]()

　　一个控件，它在界面的底部边缘显示一个或多个按钮。

#### ● [class UITabBar]()

　　一个控件，在选项卡栏（tab bar）中显示一个或多个按钮，用于在应用程序中的不同子任务，视图（view）或模式之间进行切换。

#### ● [class UITabBarItem]()

　　选项卡栏（tab bar）中的item。

#### ● [protocol UIBarPositioning]()

　　一组用于定义栏（bar）在iOS应用中的定位方式的方法。

#### ● [protocol UIBarPositioningDelegate]()

　　一组支持符合UIBarPositioning协议的栏（bar）的定位的方法。

### 八、外观定制

#### ● [protocol UIAppearance]()

　　一组方法，使你可以访问一个类的外观代理。

#### ● [protocol UIAppearanceContainer]()

　　类必须采用的协议，以允许使用UIAppearance API进行外观自定义。

### 九、相关类型

#### ● [struct UIEdgeInsets]()

　　视图（view）的偏移距离。

#### ● [struct NSDirectionalEdgeInsets]()

　　Edge insets that take language direction into account.

#### ● [struct UIOffset]()

　　定义一个结构，指定偏移位置的量。

---
## 其他内容

### 用户界面

#### ● [View Controllers]()

　　使用view controller管理你的界面，并方便导航你的应用内容。

#### ● [View布局]()

　　使用堆栈视图自动布局界面视图。需要精确放置view时，请使用“自动布局（Auto Layout）”。

#### ● [动画和触觉]()

　　使用基于view的动画和触觉为用户提供反馈。

#### ● [Windows和屏幕]()

　　为view层次结构和其他内容提供容器。