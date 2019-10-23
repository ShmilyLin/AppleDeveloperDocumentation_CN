# UIKit

构建和管理 iOS 或 tvOS 应用程序用户界面的图形，事件驱动。

---
## 概述

　　UIKit框架为你的iOS或tvOS应用程序提供所需的基础结构。它提供了用于实现界面的窗口和视图架构，用于向应用程序提供多点触控和其他类型的输入事件处理基础架构，以及管理用户、系统和应用程序之间交互所需的主运行循环。该框架提供的其他功能包括：动画支持，文档支持，绘图和打印支持，有关当前设备的信息，文本管理和显示，搜索支持，可访问性支持，应用程序扩展支持和资源管理。

> **重要**
> 
> 　　除非另有说明，否则正常来说仅从应用程序的主线程或主调度队列中使用UIKit类。此限制特别适用于从UIResponder派生的类或涉及以任何方式操纵应用程序的用户界面的类。

---
## 专题

### 一、第一步

#### ● [About App Development with UIKit]()

　　了解UIKit和Xcode为你的iOS和tvOS应用程序提供的基本支持。

## 二、应用结构

　　UIKit管理你的应用程序与系统的交互，并为你提供管理应用程序数据和资源的类。

#### ● [应用核心]()

　　管理应用的数据模型及其与系统的交互。

#### ● [资源管理]()

　　管理存储在主可执行文件外部的图像，字符串，故事板和`nib`文件。

#### ● [应用扩展]()

　　将应用程序的基本功能扩展到系统的其他部分。

### 三、用户界面

　　View可帮助你在屏幕上显示内容并促进用户交互，view controller可帮助你管理view和界面结构。

#### ● [Views和Controls](./ViewsAndControls/)

　　在屏幕上显示你的内容并定义该内容允许的交互。

#### ● [View Controllers]()

　　使用view controller管理你的界面，并方便导航你的应用内容。

#### ● [View布局]()

　　使用堆栈视图自动布局界面视图。需要精确放置view时，请使用“自动布局（Auto Layout）”。

#### ● [动画和触觉]()

　　使用基于view的动画和触觉为用户提供反馈。

#### ● [Windows和屏幕]()

　　为view层次结构和其他内容提供容器。

### 四、用户互动

　　响应者（responder）和手势识别器（gesture recognizer）可帮助你处理触摸、键盘输入和其他事件。使用拖放（drag and drop），焦点（focus），查看和弹出（peek and pop）以及辅助功能（accessibility）来处理你的内容与其他类型的用户交互。

#### ● [触摸（touch）、按压（presses）和手势（Gestures）]()

　　在手势识别器（gesture recognizer）中封装应用程序的事件处理逻辑，以便你可以在整个应用程序中重用该代码。

#### ● [拖放（drag and drop）]()

　　通过在view中使用交互API，将拖放（drag and drop）放到你的应用中。

#### ● [焦点（focus）互动]()

　　使用遥控或游戏控制器浏览UIKit应用程序的界面。

#### ● [查看和弹出（peek and pop）]()

　　使用3D Touch输入来显示内容的自定义预览和操作。

#### ● [键盘和菜单]()

　　处理键盘输入，并显示自定义操作的菜单。

#### ● [辅助功能（accessibility）]()

　　让残疾用户更方便地访问你的应用。

### 五、图形，绘图和打印

　　UIKit提供的类和协议可帮助你配置绘图环境并呈现内容。

#### ● [图像和PDF]()

　　创建和管理图像，包括使用位图和PDF格式的图像。

#### ● [绘图（drawing）]()

　　使用渲染器配置应用程序的绘图环境，并绘制路径，字符串和阴影。

#### ● [打印（printing）]()

　　显示系统打印面板并管理打印过程。

### 六、文本

　　除了可以在应用程序中轻松显示文本的文本视图（text view）外，UIKit还提供支持系统键盘的自定义文本管理和渲染。

#### ● [文本显示和字体]()

　　使用UIKit视图显示文本，管理字体和检查拼写。

#### ● [文本存储]()

　　管理文本存储，并协调文本的布局。

#### ● [键盘和输入]()

　　配置系统键盘，或自己创建自己的键盘并处理输入。

### 已弃用

　　Avoid using deprecated classes and protocols in your apps.

#### ● [Deprecated Symbols](https://developer.apple.com/documentation/uikit/deprecated_symbols)

### 参考

#### ● [UIKit Constants](https://developer.apple.com/documentation/uikit/uikit_constants)
#### ● [UIKit Data Types](https://developer.apple.com/documentation/uikit/uikit_data_types)