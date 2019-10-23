# NSOutlineView

一个用一个行列格式显示层级数据的视图，比如可以展开和折叠的目录或文件系统。



## 概述

与`table View`一样，`Outline View`不存储它展示的数据，而是从一个弱引用数据源中获取它所需要的数据（查看 [Delegates and Data Sources](https://developer.apple.com/library/etc/redirect/xcode/content/1189/documentation/General/Conceptual/CocoaEncyclopedia/DelegatesandDataSources/DelegatesandDataSources.html#//apple_ref/doc/uid/TP40010810-CH11)）。查看 `NSOutlineViewDataSource`，提供了`NSOutlineView`对象获取数据源对象中内容的方法。

一个`Outline View`有以下几个特性：

- 用户可以展开和折叠行、编辑数据、调整大小以及重排列。
- `Outline View`中的每一项必须都是唯一的。为了保持折叠状态，在重新载入时， `item`的指针需保持一致并且`item`必须使用 [`isEqual(_:)`](apple-reference-documentation://hsOBzHSzgm) 判断一致。
- 视图从一个数据源获取数据（详见`NSOutlineViewDataSource`）。
- 视图只会获取需要被展示的数据。



> **重要**
>
> 如果在Interface Builder中指定数据源，那么给`Outline View`提供你的数据源的方法有可能会在[`awakeFromNib()`](apple-reference-documentation://hskwxWFeJR)之前被调用。你需要在数据源的数据尚未初始化之前，通过给数据源的[`outlineView(_:numberOfChildrenOfItem:)`](apple-reference-documentation://hslmkEXDA6) 方法返回`0`来防止这种情况发生。在[`awakeFromNib()`](apple-reference-documentation://hskwxWFeJR)中，当数据源中的数据已经被初始化，你需要调用[`reloadData()`](apple-reference-documentation://hsKSk5X8Op)。



### 子类

不推荐使用`NSOutlineView`的子类。自定义可以在你的数据源的类中实现（遵守`NSOutlineViewDataSource`）或者在你的`delegate`中实现（遵守`NSOutlineViewDelegate`）。



## 讲解

### 访问数据源

#### var dataSource: NSOutlineViewDataSource?

这个对象提供接收器显示的数据。

###### 声明

```swift
weak var dataSource: NSOutlineViewDataSource? { get set }
```

###### 解释

The object must implement the appropriate methods of [`NSOutlineViewDataSource`](apple-reference-documentation://hsnolATOM9). See [Writing an Outline View Data Source](https://developer.apple.com/library/etc/redirect/xcode/content/1189/documentation/Cocoa/Conceptual/OutlineView/Articles/UsingOutlineDataSource.html#//apple_ref/doc/uid/20000725) and the NSOutlineViewDataSource Protocol informal protocol specification for more information. Note that in versions of macOS prior to v10.12, the outline view did not retain the data source in a managed memory environment.

Setting the data source invokes [`tile()`](apple-reference-documentation://hsm6XC_gTY).

如果数据源没有响应所有的 [`outlineView(_:child:ofItem:)`](apple-reference-documentation://hsjVoTVD85), [`outlineView(_:isItemExpandable:)`](apple-reference-documentation://hsBJJNpSgI)、[`outlineView(_:numberOfChildrenOfItem:)`](apple-reference-documentation://hslmkEXDA6)和[`outlineView(_:objectValueFor:byItem:)`](apple-reference-documentation://hsVYVPrE_z)方法，那么一个[`internalInconsistencyException`](apple-reference-documentation://hs9EOkTV06) 可能会被触发。



#### var stronglyReferencesItems: Bool

`Outline View`是保存还是释放数据源返回的对象。

###### 声明

```swift
var stronglyReferencesItems: Bool { get set }
```

###### 解释

当这个属性的值为`true`时，`Outline View`保存和释放从`dataSource`返回的对象。当这个值为`false`时，`Outline View`将对象作为不可保留项处理并认为客户端有保存。这个属性的默认值在macOS10.12及其之后版本的系统中为`true`，在其之前的版本中为`false`。如果你想在macOS10.12或其之后版本的系统中使用已经废弃的行为事件，这个属性的值必须使用代码显示的设置为`false`，因为这个值在`nib`文件中不会被编译。通常情况下，就要求了他们自己创建一个保存副本。



---

### 展开

#### func isExpandable(Any?)

获取给定的`Item`是否可以被展开。

###### 声明

```swift
func isExpandable(_ item: Any?) -> Bool
```

###### 参数

* **item**

  接收器中的一个`Item`

###### 返回值

`true`表示给定的`Item`可以被展开——这表示`Item`中可以包含其他的`Items`，否则返回`false`。



#### func isItemExpanded(Any?)

获取给定的`Item`是否已经被展开。

######声明

```swift
func isItemExpanded(_ item: Any?) -> Bool
```

###### 参数

- **item**

  接收器中的一个`Item`

###### 返回值

`true`表示给定的`Item`已经被展开，否则返回`false`。



---

### Outline的展开和折叠

#### func expandItem(Any?)

展开一个给定的`Item`。

###### 声明

```swift
func expandItem(_ item: Any?)
```

###### 参数

* **item**

  接收器中的一个`Item`

###### 解释

如果`item`不允许被展开或者已经被展开，将不会做任何操作。

如果开始展开，则会发出`Item`展开的通知。



#### func expandItem(Any?, expandChildren: Bool)

展开一个指定的`Item`，并且可以选择是否展开它的子项。

###### 声明

```swift
func expandItem(_ item: Any?, expandChildren: Bool)
```

###### 参数

* **item**

  接收器中的一个`Item`。

  从OX 10.5开始，传入`nil`将会展开`outline View`的根节点下面的每一个`Item`。

* **expandChildren**

  如果为`true`，则会递归的展开这个`Item`及其子项。如果为`false`，只展开这个`Item`（等同于[`expandItem(_:)`](#func-expanditemany)）。


###### 解释

例如，当用户点击`Outline View`中的一个`Item`的三角形的时候，便会调用这个方法，并给参数`expandChildren` 传入`true`（展开这个`Item`以及它包含的所有`Item`）。

每个`Item`的展开都会发出一个`Item`展开的通知。



#### func collapseItem(Any?)

折叠一个给定的`Item`。

###### 声明

```swift
func collapseItem(_ item: Any?)
```

###### 参数

* **item**

  接收器中的一个`Item`。

###### 解释

如果`item`没有展开活着不允许展开，将不会做任何操作。

如果开始折叠，则会发出`Item`折叠的通知。



#### func collapseItem(Any?, collapseChildren: Bool)

折叠一个给定的`Item`，并且可以选择是否折叠它的子项。

###### 声明

```swift
func collapseItem(_ item: Any?, collapseChildren: Bool)
```

###### 参数

* **item**

  接收器中的一个`Item`。

  从OX 10.5开始，传入`nil`将会折叠`outline View`的根节点下面的每一个`Item`。


* **collapseChildren**

  如果为`true`，则会递归的折叠这个`Item`及其子项。如果为`false`，只折叠这个`Item`（等同于[`collapseItem(_:)`](#func-collapseitemany)）。

###### 解释

例如，当用户点击`Outline View`中的一个`Item`的三角形的时候，便会调用这个方法，并给参数`collapseChildren` 传入`true`（折叠这个`Item`以及它包含的所有`Item`）。

每个`Item`的折叠都会发出一个`Item折叠的通知。



---

### 重新显示信息

#### func reloadItem(Any?)

重新加载和显示给定的`Item`中的数据。

###### 声明

```swift
func reloadItem(_ item: Any?)
```

###### 参数

* **item**

  要重新加载和显示的`Item`。

###### 解释

Reloading the cell views associated with `item` occurs only in apps that link against macOS 10.12 and later. 

This method may cause the outline view to change its selection without calling the [`outlineViewSelectionDidChange(_:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdelegate/1526913-outlineviewselectiondidchange) delegate method. 



#### func reloadItem(Any?, reloadChildren: Bool)

重新加载和显示给定的`Item`中的数据，并且可以选择是否也重新加载和显示它的子项。

###### 声明

```swift

```

###### 参数

###### 解释



---

### 项和行之间的转换



#### func item(atRow: Int)

返回与给定行相关联的`Item`。

###### 声明

```swift
func item(atRow row: Int) -> Any?
```

###### 参数

* **row**

  接收器的行号

###### 返回值

与行相关联的`Item`



####  func row(forItem: Any?)

与给定的`Item`相关联的行。

###### 声明

```swift
func row(forItem item: Any?) -> Int
```

###### 参数

* **item**

  接收器中的一个`Item`。

###### 返回值

与`Item`相关联的行，如果`item`为`nil`或者在`Outline View`中没有找到则返回-1。



---

### Outline的列

#### var outlineTableColumn: NSTableColumn?

显示层级数据的列。

###### 声明

```swift
unowned(unsafe) var outlineTableColumn: NSTableColumn? { get set }
```

###### 解释

层级数据的每一层的缩进通过`indentationPerLevel`属性指定（默认值为`16`），每个可以展开的行都带有缩进标记（三角形）。`Outline View`的行数据与其视图状态信息一起保存。

如果将这个属性的值设置为`nil`，则将会忽略这个属性。



#### var autoresizesOutlineColumn: Bool

当用户展开或者折叠`Outline View`中的`Items`的时候，`Outline View`是否自动调整大小。

###### 声明

```swift
var autoresizesOutlineColumn: Bool { get set }
```

###### 解释

`Outline View`的列包含多个有展开标志的`cells`，并且通常还是第一列。这个属性的默认值为`true`，意味着`Outline View`会自动调整列的大小。

`Outline View`的列调整的大小取决于缩进等级以及展开还是折叠的状态。例如，一个展开的行是一个缩进等级，`Outline View`的列的宽度将增加一个`indentationPerLevel`大小。



---

### 缩进

#### func level(forItem: Any?)

返回给定`Item`的缩进等级。

###### 声明

```swift
func level(forItem item: Any?) -> Int
```

###### 参数

* **item**

  接收器中的一个`Item`。

###### 返回值

`Item`的缩进等级。如果`Item`为`nil`（表示根节点），则返回-1。

###### 解释

等级是以`0`为起始的——显示的第一等级的`Item`返回来的值是`0`。



#### func level(forRow: Int)

返回给定的行的缩进等级。

###### 声明

```swift
func level(forRow row: Int) -> Int
```

###### 参数

* **row**

  接收器的行的行号。

###### 返回值

行的缩进等级。无效的行则返回-1。

###### 解释

等级是以`0`为起始的——显示的第一等级的`Item`返回来的值是`0`。



#### var indentationPerLevel: CGFloat

每个等级的缩进量，以点为单位。

###### 声明

```swift
var indentationPerLevel: CGFloat { get set }
```



#### var indentationMarkerFollowsCell: Bool

在`Outline View`的列中显示的缩进标记是否跟随`cell`的内容一起缩进。

###### 声明

```swift
var indentationMarkerFollowsCell: Bool { get set }
```

###### 解释

当这个属性的值为`true`时，缩进标记跟随`cell`内容一起缩进。当这个值为`false`的时候，缩进标记总显示在列的最左侧。这个属性的默认值为`true`。



---

### 持久化

#### var autosaveExpandedItems: Bool

应用程序启动过程中展开的`Item`是否自动保存。

###### 声明

```swift
var autosaveExpandedItems: Bool { get set }
```

###### 解释

当这个属性的值为`true`时，`Outline View`保存其展开的`Item`的状态，并在下次用户启动应用时恢复这个状态。（如果`Outline View`的`autosaveName`属性为`nil`，或者如果你没有实现[`outlineView(_:itemForPersistentObject:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1533602-outlineview)和[`outlineView(_:persistentObjectForItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1532545-outlineview)两个协议方法，这个属性的设置将会被忽略，并且将不会存储状态。）这个配置数据将会给每个用户的每个应用单独存储。这个属性的默认值为`false`。

你可以单独设置 [`autosaveExpandedItems`](https://developer.apple.com/documentation/appkit/nsoutlineview/1530638-autosaveexpandeditems) and [`autosaveTableColumns`](https://developer.apple.com/documentation/appkit/nstableview/1525596-autosavetablecolumns) 属性，这样你就可以做一些其他的事情，比如说，保存展开的`Item`的信息，但是不保存列的位置。



---

### 支持拖放

#### func setDropItem(Any?, dropChildIndex: Int)

Used to “retarget” a proposed drop.

###### 声明

```swift
func setDropItem(_ item: Any?, dropChildIndex index: Int)
```

###### 参数

* **item**

  目标`Item`。

* **index**

  放下的位置。

###### 解释

例如，想要指定放`someOutlineItem`，你设定`item`为`someOutlineItem`，`index`为[`NSOutlineViewDropOnItemIndex`](https://developer.apple.com/documentation/appkit/nsoutlineviewdroponitemindex)。想要讲`someOutlineItem`指定放在子项的`2`和`3`之间，你设定`item`为`someOutlineItem`，`index`为`3`（子项是以`0`为初始序号的）。想要放一个不允许展开的`someOutlineItem`，你设定`item`为`someOutlineItem`，`index`为`NSOutlineViewDropOnItemIndex`。



#### func shouldCollapseAutoExpandedItems(forDeposited: Bool)

自动展开的`Items`是否返回它们原来的折叠状态。

###### 声明

```swift
func shouldCollapseAutoExpandedItems(forDeposited deposited: Bool) -> Bool
```

###### 参数

* **deposited**

  如果为`true`，放入成功结束；如果为`false`则放入失败。

###### 返回值

如果自动展开的`Items`需要返回它们原始的折叠状态则返回`true`，否则返回`false`。

###### 解释

重写这个方法来提供自定义行为事件。如果放入的目标不是自动展开的（悬停时间足够长），放入目标会在放入成功后一直处于展开状态，除非这个方法返回`true`。放入成功后默认实现返回`false`。

这个方法在各种情况下都会被调用。例如，在[`outlineView(_:acceptDrop:item:childIndex:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1529572-outlineview) 方法被调用后会立刻调用这个方法，并且拖出`Outline View`（拖出视图会被当作一个失败的放入）也会被调用。`outlineView(_:acceptDrop:item:childIndex:)`方法的返回值决定了`deposited`属性进来时候的值。



---

### 获取相关的`Items`

#### func parent(forItem: Any?)

返回给定`Item`的父级。

###### 声明

```swift
func parent(forItem item: Any?) -> Any?
```

###### 参数

* **item**

  要返回父级的`Item`。

###### 返回值

`item`的父级，如果父级为根结点则返回`nil`。



#### func childIndex(forItem: Any)

返回给定的`Item`在其父级中的索引值（译者注：即位置）。

###### 声明

```swift
func childIndex(forItem item: Any) -> Int
```

###### 解释

这个方法最好性能是 O(1)，最差性能是 O(n)。



#### func child(Int, ofItem: Any?)

返回一个`Item`的指定的子项。

###### 声明

```swift
func child(_ index: Int, ofItem item: Any?) -> Any?
```

###### 参数

* **index**

  子项在其父级中的索引值。

* **item**

  你想要获取的子项的父级`Item`。

###### 返回值

子项，如果没有找到这个子项则返回`nil`。

###### 解释

你可以在使用一个静态或动态数据预案的`Outline View`中调用这个方法。动态内容的`Outline View`中，这个方法可能会调用相关联的数据源对象的[`outlineView(_:child:ofItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1528977-outlineview)方法。



#### func numberOfChildren(ofItem: Any?)

返回给定的父级`Item`它所包含的子项的数量。

###### 声明

```swift
func numberOfChildren(ofItem item: Any?) -> Int
```

###### 参数

* **item**

  父级`Item`。

###### 返回值

与父级关联的子项的数量。

###### 解释

你可以在使用一个静态或动态数据预案的`Outline View`中调用这个方法。动态内容的`Outline View`中，这个方法可能会调用相关联的数据源对象的[`outlineView(_:numberOfChildrenOfItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1535549-outlineview)方法。



---

### 获取`cell`的`frame`

#### func frameOfOutlineCell(atRow: Int)

返回给定行的`cell`的`frame`。

###### 声明

```swift
func frameOfOutlineCell(atRow row: Int) -> NSRect
```

###### 参数

* **row**

  要返回`frame`的行号。

###### 返回值

`row`所指定的行的`cell`的`frame`，包括当前缩进和[`indentationMarkerFollowsCell`](https://developer.apple.com/documentation/appkit/nsoutlineview/1531707-indentationmarkerfollowscell)属性的值。如果`row`指定的行不是一个可以展开的行，则返回`NSZeroRect`。

###### 解释

你可以在子类中重写这个方法来为`Outline View`的`Cell`返回一个自定义的`frame`。如果你宠妾并返回一个空的`rect`，则这一行则不会绘制`cell`。你可以这样做，比如，这样这一行的三角形就不会被显示并且永远不会被展开。



---

### 代理授权

#### var delegate: NSOutlineViewDelegate?

`Outline View`的`delegate`。

###### 声明

```swift
weak var delegate: NSOutlineViewDelegate? { get set }
```

###### 解释

The delegate must conform to the [`NSOutlineViewDelegate`](https://developer.apple.com/documentation/appkit/nsoutlineviewdelegate) protocol. Note that in versions of macOS prior to v10.12, the table view did not retain the delegate in a managed memory environment.



---

### 操作`Items`

#### func insertItems(at: IndexSet, inParent: Any?, withAnimation: NSTableView.AnimationOptions = [])

在给定的父类中的指定位置上插入新的`Items`，并设置插入时的动画。

###### 声明

```swift
func insertItems(at indexes: IndexSet, inParent parent: Any?, withAnimation animationOptions: NSTableView.AnimationOptions = [])
```

###### 参数

* **indexes**

  插入的`Items`的索引值（译者注：即在父级中的位置）。


* **parent**

  要插入的`Items`的父级，如果为`nil`则表示在最顶层中插入。


* **animationOptions**

  插入`Items`时显示的动画效果。

###### 解释

这个方法类似于`NSTableView`的[`insertRows(at:withAnimation:)`](https://developer.apple.com/documentation/appkit/nstableview/1532406-insertrows)方法，用法上和`NSMutableArray`的 [`insert(_:at:)`](https://developer.apple.com/documentation/foundation/nsmutablearray/1416482-insert)方法一样。如果父级不允许展开，则这个方法将会什么都不会操作。实际插入的真正的`Items`由数据源的[`outlineView(_:child:ofItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1528977-outlineview)方法（这个方法只会在[`endUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1526267-endupdates)之后被调用以确保数据源的完整）提供。

>  **注意**
>
> 基于`NSCell`的`Outline View`在调用此方法之前必须调用[`beginUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1527288-beginupdates)。

你可以在同一个 [`beginUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1527288-beginupdates)/[`endUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1526267-endupdates)代码块中多次调用这个方法；新插入的`Items`会移动之前插入的新`Items`，就像修改一个数组一样。如果插入的索引值超出可用范围（译者注：俗称越界），则会抛出一个异常。



#### func moveItem(at: Int, inParent: Any?, to: Int, inParent:Any?)

移动一个给定的父级中位置的`Items`到另一个父级中的位置。

###### 声明

```swift
func moveItem(at fromIndex: Int, inParent oldParent: Any?, to toIndex: Int, inParent newParent: Any?)
```

###### 参数

* **fromIndex**

  要被移动的`Item`的索引值。


* **oldParent**

  要被移动的`Item`的父级。


* **toIndex**

  `Item`移动后的索引值。


* **newParent**

  `Item`移动后的父级。

###### 解释

这个方法与`NSTableView`的[`moveRow(at:to:)`](https://developer.apple.com/documentation/appkit/nstableview/1535835-moverow)方法类似。`newParent`可以和`oldParent`相同来重新排列`Item`。

>  **注意**
>
> 基于`NSCell`的`Outline View`在调用此方法之前必须调用[`beginUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1527288-beginupdates)。

你可以在同一个 [`beginUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1527288-beginupdates)/[`endUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1526267-endupdates)代码块中多次调用这个方法。移动一个无效的索引值，或移动到一个无效的索引值，会抛出一个异常。



#### func removeItems(at: IndexSet, inParent: Any?, withAnimation: NSTableView.AnimationOptions = [])

在给定的父类中的指定位置上移除`Items`，并设置移除时的动画。

###### 声明

```swift
func removeItems(at indexes: IndexSet, inParent parent: Any?, withAnimation animationOptions: NSTableView.AnimationOptions = [])
```

###### 参数

* **indexes**

  要被移除的`Items`的索引值。


* **parent**

  要被移除的`Items`的父级。

* **animationOptions**

  移除Items`时显示的动画效果。

###### 解释

这个方法同`NSTableView`的[`removeRows(at:withAnimation:)`](https://developer.apple.com/documentation/appkit/nstableview/1524655-removerows)方法类似，用法与`NSMutableArray`的[`removeObjects(at:)`](https://developer.apple.com/documentation/foundation/nsmutablearray/1410154-removeobjects)方法一样。如果`parent`不允许展开则这个方法将不会做任何处理。如果被删除的`Item`有子项被展开，那么所有子项也会被移除。

>  **注意**
>
> 基于`NSCell`的`Outline View`在调用此方法之前必须调用[`beginUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1527288-beginupdates)。

你可以在同一个 [`beginUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1527288-beginupdates)/[`endUpdates()`](https://developer.apple.com/documentation/appkit/nstableview/1526267-endupdates)代码块中多次调用这个方法；就像修改一个数组一样工作。如果移除一个超出范围的索引值则会抛出一个异常。



---

### 用户界面布局方向

#### var userInterfaceLayoutDirection: NSUserInterfaceLayoutDirection

###### 声明

```swift
var userInterfaceLayoutDirection: NSUserInterfaceLayoutDirection { get set }
```

###### 解释

当设置为[`rightToLeft`](https://developer.apple.com/documentation/appkit/nsuserinterfacelayoutdirection/1396112-righttoleft)，三角形显示在`Outline View`的`cell`的右侧而不是左侧。默认值为[`leftToRight`](https://developer.apple.com/documentation/appkit/nsuserinterfacelayoutdirection/1396104-lefttoright)。



---

### 常量

#### [放下`Item`的索引值](./DropOnItemIndex.md)

这个常量定义了一个索引值，允许你直接将Item放在目标上。



#### [`Outline View`按钮键](./OutlineViewButtonKeys.md)

`Outline View`用这些键创建展开和折叠`Items`的按钮。



---

### 通知

```
class let columnDidMoveNotification: NSNotification.Name
```

Posted whenever a column is moved by user action in an `NSOutlineView`object.

```
class let columnDidResizeNotification: NSNotification.Name
```

Posted whenever a column is resized in an `NSOutlineView` object.

```
class let itemDidCollapseNotification: NSNotification.Name
```

Posted whenever an item is collapsed in an `NSOutlineView` object.

```
class let itemDidExpandNotification: NSNotification.Name
```

Posted whenever an item is expanded in an `NSOutlineView` object.

```
class let itemWillCollapseNotification: NSNotification.Name
```

Posted before an item is collapsed (after the user clicks the arrow but before the item is collapsed).

```
class let itemWillExpandNotification: NSNotification.Name
```

Posted before an item is expanded (after the user clicks the arrow but before the item is collapsed).

```
class let selectionDidChangeNotification: NSNotification.Name
```

Posted after the outline view's selection changes.

```
class let selectionIsChangingNotification: NSNotification.Name
```

Posted as the outline view’s selection changes (while the mouse button is still down).



## 关联

### 继承自

[`NSTableView`](apple-reference-documentation://hs_JTB0H3I)

### Conforms To

- [`CVarArg`](apple-reference-documentation://hs16nXL9Fo)
- [`Equatable`](apple-reference-documentation://hs-MXxh1WG)
- [`Hashable`](apple-reference-documentation://hsx4S2g0iZ)

