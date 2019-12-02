# Cocoa Bindings

使用`Cocoa Bindings`自动将数据模型与应用程序界面同步。

## 主题

### 核心控制器

* [class NSObjectController]()

    可以管理键值路径引用的对象属性的控制器。

* [class NSController]()

    实现控制器类所需的[NSEditor]()和[NSEditorRegistration]()非正式协议的抽象类。

### 树型数据

* [使用`Outline View`和`Split View`导航分层数据](./navigating_hierarchical_data_using_outline_and_split_views.md)

构建结构化的用户界面，以简化App中的导航。

* [class NSTreeController]()
A bindings-compatible controller that manages a tree of objects.

* [class NSTreeNode]()
A node in a tree of nodes.

### 数组型数据

* [class NSArrayController]()
A bindings-compatible controller that manages a collection of objects.

### 键值对型数据

* [class NSDictionaryController]()
A bindings-compatible controller that manages the display and editing of a dictionary of key-value pairs.

* [class NSDictionaryControllerKeyValuePair]()
A set of methods implemented by arranged objects to give access to information about those objects.

* [NSKeyValueBindingCreation]()
A set of methods that you can use to create and remove bindings between view objects and controllers, or between controllers and model objects.

### 数据占位符

* [NSPlaceholders]()
A set of methods that an object can implement to register default placeholders to be displayed for a binding, when no other placeholder is specified.