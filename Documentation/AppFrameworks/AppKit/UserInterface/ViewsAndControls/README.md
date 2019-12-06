# Views and Controls

在屏幕上显示你的内容并定义这些内容的交互。

## 主题

### 基本原理

* [class NSView](./ViewFundamentals/NSView/)

一个App中绘制、打印和事件处理的基础。

* [class NSControl](./ViewFundamentals/NSControl/)

`Control`的基本行为的定义，这些`Control`是一种特殊的`View`，可通过使用`Target-Action`设计模式将相关事件通知给你的App。

* [class NSCell](./ViewFundamentals/NSCell/)

一个用于在一个`View`对象上显示文本或图片的结构，并且不需要一个完整的`NSView`子类的开销。

* [class NSActionCell](./ViewFundamentals/NSActionCell/)

`Control`内的一个活动区域。

### 容器视图

使用容器视图排列你的界面中的视图，并且使得这些视图之间更容易联系。

* [网格视图]

在一个灵活的网格中排列视图，并处理和这些视图相关的布局。

* [class NSSplitView](./ContainerViews/NSSplitView.md)

在一个水平或竖直的线性堆中排列两个或多个视图的视图。

* [class NSStackView]

水平或垂直的排列一组视图的视图，并且当窗口大小改变的时候自动更新它们的位置和大小。

* [class NSTabView]

一个在同一时刻只展示一个页面的多页面界面。

* [Scroll View]

因为导航内容过大而无法在有效的控件内展示，而提供的一个可以滚动的界面。

### 内容视图

使用内容视图来组织和显示你应用的数据。

* [Browser View]

为展示和导航层次信息而提供一个基于列的界面。

* [Collection View](./ContentViews/CollectionView/CollectionView.md)

在一个高度可配置的排列中展示一个或多个子视图。

* [Outline View](./ContentViews/OutlineView/OutlineView.md)

将层级数据以列表的形式展示出来，每一个层级相对于前一个层级都有一定的缩进距离。

* [class NSOpenGLView]

在一个视图中展示OpenGL内容的视图。

* [Table View](./ContentViews/TableView/TableView.md)

在行和列中显示自定义数据。

* [class NSTextView]

A view that draws text and handles user interactions with that text. 



### 控件

Use controls to handle specific types of user interactions. Controls are specialized views that use the target-action design pattern to notify your app of interactions with their content.

* [class NSButton](./Controls/NSButton/)

定义屏幕上可用于触发动作的区域的控件。

* [class NSColorWell]

A control that displays a color value and lets the user change that color value. 

* [Date Picker]

Display a calendar date and provide controls for editing the date value. 

* [class NSImageView]

A display of image data from an [`NSImage`](https://developer.apple.com/documentation/appkit/nsimage) object in a frame. 

* [class NSLevelIndicator]

A visual representation of a level or quantity, using discrete values.

* [Path Control]

A display of a file system path or virtual path information.

* [class NSPopUpButton]

A display of a single item from a list of items, and provide an interface for selecting items from the list.  

* [class NSProgressIndicator]

An interface that provides visual feedback to the user about the status of an ongoing task. 

* [class NSRuleEditor]

An interface for configuring a rule-based list of options. 

* [class NSPredicateEditor]

A defined set of rules that allows the editing of predicate objects.

* [Search Field]

Provide a text field that is optimized for text-based search interfaces.  

* [class NSSegmentedControl]

Display one or more buttons in a single horizontal group. 

* [Slider]

Display a range of values from which the user selects a single value. 

* [class NSStepper]

An interface with up and down arrow buttons for incrementing or decrementing a value.

* **[Text Field]**

Provide a simple interface for displaying and editing text, including support for password fields and secure forms of text entry.  

* **[Token Field]**

Provide a text field whose text can be rendered in a visually distinct way so that users can recognize portions more easily. 

* **[Toolbar]**

Provide a space for controls under a window's title bar and above your custom content.    

* **[Combo Box]**

Display a list of values in a pop-up menu that lets the user select a value or type in a custom value. 

* **[class NSMatrix]**

A legacy interface for grouping radio buttons or other types of cells together. 



### Visual Adornments

Add purely decorative elements to your user interface.

* **[class NSBox]**

A stylized rectangular box with an optional title.

* **[class NSVisualEffectView]**

A view that adds translucency and vibrancy effects to the views in your interface. 



### View Layout

* **[class NSLayoutConstraint]**

The relationship between two user interface objects that must be satisfied by the constraint-based layout system. 

* **[class NSLayoutGuide]**

A rectangular area that can interact with Auto Layout. 

* **[class NSLayoutDimension]**

A factory class for creating size-based layout constraint objects using a fluent API. 

* **[class NSLayoutAnchor]**

A factory class for creating layout constraint objects using a fluent API. 

* **[class NSLayoutXAxisAnchor]**

A factory class for creating horizontal layout constraint objects using a fluent API.

* **[class NSLayoutYAxisAnchor]**

A factory class for creating vertical layout constraint objects using a fluent API.



### Appearance Customization

Apply standard themes to the views in your interface.

* **[class NSAppearance]**

An object that manages standard appearance attributes for UI elements in an app.

* **[protocol NSAppearanceCustomization]**

A set of methods for getting or setting the appearance attributes of a view. 



### UI Validation

* **[protocol NSUserInterfaceValidations]**

A protocol that a custom class can adopt to manage the enabled state of a UI element.

* **[protocol NSValidatedUserInterfaceItem]**

A protocol that a custom class can adopt to manage the automatic enablement of a UI control.



### Tool Tips

* **[NSToolTipOwner]**

A set of methods for dynamically associating a tool tip with a view. 



## See Also

### User Interface

View Management

Manage your user interface, including the size and position of views in a window. 

Menus, Cursors, and the Dock

Implement menus and cursors to facilitate interactions with your app, and use your app's Dock tile to convey updated information. 

Windows, Panels, and Screens

Organize your view hierarchies and facilitate their display onscreen. 

Accessibility

Make your app more accessible to users with disabilities.

Touch Bar

Display interactive content and controls in the Touch Bar. 

Animation

Animate your views and other content to create a more engaging experience for users. 

Drag and Drop

Support the direct manipulation of your app's content using drag and drop. 

Sound, Speech, and Haptics

Play sounds and haptic feedback, and incorporate speech recognition and synthesis into your interface.