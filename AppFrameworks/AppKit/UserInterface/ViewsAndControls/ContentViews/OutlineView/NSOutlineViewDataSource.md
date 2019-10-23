# NSOutlineViewDataSource

`Outline View`调用，用来从数据源协议中接受数据以及关于数据的信息的一组方法，并且也可以选择更新数据的值。



## 概述

除标准的`delegate`对象之外，[`NSOutlineView`](./NSOutlineView.md)对象还支持一个数据源协议。

`NSOutlineViewDataSource`协议中的所有方法都被标记了`@optional`。虽然是这样，但是有些情况你必须实现一些方法来获取所需要的功能，特别是当处理常规数据源而不是可绑定的数据源的时候。



### Required and Optional Methods Using Programmatic Conventions and Cocoa Bindings

If you are using conventional data sources for content you must implement the basic methods that provide the outline view with data: [`outlineView(_:child:ofItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1528977-outlineview), [`outlineView(_:isItemExpandable:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1535198-outlineview), [`outlineView(_:numberOfChildrenOfItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1535549-outlineview), and [`outlineView(_:objectValueFor:byItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1531606-outlineview). Applications that acquire their data using Cocoa bindings do not need to implement these methods.

Similarly, when using conventional data sources , if you want to allow the user to edit values, you must implement [`outlineView(_:setObjectValue:for:byItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1534817-outlineview). When these methods are invoked by the outline view, `nil` as the `item` refers to the “root” item. `NSOutlineView` requires that each item in the outline view be unique. In order for the collapsed state of an outline view to remain consistent between reloads you must always return the same object for an item. When using Cocoa bindings to provide outline view content, there is no requirement to implement this method.



> **注意**
>
> Some of the methods in this `protocol`, such as [`outlineView(_:child:ofItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1528977-outlineview)and [`outlineView(_:numberOfChildrenOfItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1535549-outlineview) along with other methods that return data, are called very frequently, so they must be efficient.



## 讲解

### 实例方法

#### func outlineView(NSOutlineView, acceptDrop: NSDraggingInfo, item: Any?, childIndex: Int)

返回放入操作是否成功。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, acceptDrop info: NSDraggingInfo, item: Any?, childIndex index: Int) -> Bool
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。`outlineView` 在之前必须允许放入操作。

* **info**

  包含了这个放入操作的更多信息的对象。

* **item**

  鼠标松开时，鼠标指针指向的`Item`的父级。

* **index**

  鼠标松开时，鼠标指针指向的`Item`的子项索引值。

###### 返回值

如果放入操作成功则返回`true`，否则返回`false`。

###### 解释

数据源需要包含在这个方法的实现中的拖拽剪贴板中的数据，你可以在放入操作的`info`中使用[`draggingPasteboard()`](https://developer.apple.com/documentation/appkit/nsdragginginfo/1416092-draggingpasteboard)方法得到这个数据。

返回值表示系统的拖拽操作是否成功。



#### func outlineView(NSOutlineView, child: Int, ofItem: Any?)

返回给定`item`的索引值位置的子项。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, child index: Int, ofItem item: Any?) -> Any
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。

* **index**

  `item`的子项索引值。

* **item**

  一个数据源中的`item`。

###### 返回值

`item`的`index`位置的子项。如果`item`为`nil`，则返回最顶层的子项。

###### 解释

会顺序访问给定的父级`item`的子项。为了保持`Outline View`的折叠状态一致，当它重载时，对于指定的`child`和`item`你必须总是返回同一个对象。

> **重要**
>
> 虽然这个方法在协议中被标记为`@optional`，**如果你没有使用绑定数据给`Outline View`提供数据，那么你必须实现这个方法。**在这个方法中不要调用[`reloadData()`方法。

###### 特别注意事项

[`outlineView(_:child:ofItem:)`](#func_outlineviewnsoutlineview_child_int_ofitem_any)方法会被非常频繁的调用，所以一定要保证它是高效的。



#### func outlineView(NSOutlineView, draggingSession: NSDraggingSession, endedAt: NSPoint, operation: NSDragOperation)

实现这个方法可以知道给定的拖动会话何时结束。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, draggingSession session: NSDraggingSession, endedAt screenPoint: NSPoint, operation: NSDragOperation)
```

###### 参数

* **outlineView**

  拖动开始的`Outline View`。

* **session**

  结束的拖动会话。

* **screenPoint**

  拖动结束时在屏幕上的位置。

* **operation**

  指定了拖动源允许的拖动操作的掩码。

###### 解释

你可以实现这个可选的协议方法来知道拖动源操作在某个位置结束，例如垃圾箱（通过检查 [`delete`](https://developer.apple.com/documentation/appkit/nsdragoperation/1416064-delete)操作）。



#### func outlineView(NSOutlineView, draggingSession: NSDraggingSession, willBeginAt: NSPoint, forItems: [Any])

实现这个方法来可以知道给定的拖拽会话何时将要开始，并可以修改这个拖拽会话。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, draggingSession session: NSDraggingSession, willBeginAt screenPoint: NSPoint, forItems draggedItems: [Any])
```

###### 参数

* **outlineView**

  拖拽将要开始的`Outline View`。


* **session**

  将要开始的拖拽会话。


* **screenPoint**

  将要开始的拖拽开始的屏幕位置。


* **draggedItems**

  被拖动的`Items`的数组，不包括[`outlineView(_:pasteboardWriterForItem:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1525837-outlineview)方法返回`nil`的`Items`。

###### 解释

The `draggedItems` array directly matches the pasteboard writer array used to begin the dragging session with the `NSView` method [`beginDraggingSession(with:event:source:)`](https://developer.apple.com/documentation/appkit/nsview/1483791-begindraggingsession). Hence, the order is deterministic, and can be used in [`outlineView(_:acceptDrop:item:childIndex:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1529572-outlineview) when enumerating the `NSDraggingInfo` protocol's pasteboard classes.



#### func outlineView(NSOutlineView, isItemExpandable: Any)

返回一个表示给定`Item`是否可以被展开的布尔值。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, isItemExpandable item: Any) -> Bool
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。


* **item**

  数据源中的`Item`。

###### 返回值

如果可以展开显示它的子项则返回`true`，否则返回`false`。

###### 解释

这个方法会被经常的调用，所以一定要保证它是高效的。

> **重要**
>
> 虽然这个方法在协议中被标记为`@optional`，**如果你没有使用绑定数据给`Outline View`提供数据，那么你必须实现这个方法。**在这个方法中不要调用[`reloadData()`方法。



#### func outlineView(NSOutlineView, itemForPersistentObject: Any)

Invoked by `outlineView` to return the item for the archived `object`.

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, itemForPersistentObject object: Any) -> Any?
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。

* **object**

  `Outline View`的数据源中的一个对象的存档后的表现形式。

###### 返回值

与`object`对应的非存档的`item`。如果这个`item`是一个存档了的对象，这个方法会返回这个对象。

###### 解释

当`Outline View`恢复保存的展开的`Items`时，这个方法为每个展开的`Item`调用，来将存档的对象转换为`Outline View`的`Item`。

###### 特别注意事项

如果你自动存储了展开的`Items`（即[`autosaveExpandedItems`](https://developer.apple.com/documentation/appkit/nsoutlineview/1530638-autosaveexpandeditems)返回`true`时），那么你必须实现这个方法。 



#### func outlineView(NSOutlineView, numberOfChildrenOfItem: Any?)

返回给定的`item`中包含的子项的数量。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, numberOfChildrenOfItem item: Any?) -> Int
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。

* **item**

  数据源中的一个`Item`。

###### 返回值

`item`中包含的子项的数量。如果`item`为`nil`，这个方法应该返回最顶层的子项的数量。

###### 解释

 [`outlineView(_:numberOfChildrenOfItem:)`](#func_outlineviewnsoutlineview_numberofchildrenofitem_any)方法会被非常频繁的调用，所以一定要保证它是高效的。

> **重要**
>
> 虽然这个方法在协议中被标记为`@optional`，**如果你没有使用绑定数据给`Outline View`提供数据，那么你必须实现这个方法。**在这个方法中不要调用[`reloadData()`方法。



#### func outlineView(NSOutlineView, objectValueFor: NSTableColumn?, byItem: Any?)



Invoked by `outlineView` to return the data object associated with the specified `item`.

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, objectValueFor tableColumn: NSTableColumn?, byItem item: Any?) -> Any?
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。


* **tableColumn**

  `outlineView`中的一列。


* **item**

  视图中给定的`tableColumn`中数据源中的一个`item`。

###### 解释

`item`位于视图中给定的`tableColumn`中。

> **重要**
>
> 虽然这个方法在协议中被标记为`@optional`，**如果你没有使用绑定数据给`Outline View`提供数据，那么你必须实现这个方法。**在这个方法中不要调用`reloadData()`方法。



#### func outlineView(NSOutlineView, pasteboardWriterForItem: Any)

实现这个方法可以允许表作为一个支持多个`Items`的拖放的`NSDraggingSource`。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, pasteboardWriterForItem item: Any) -> NSPasteboardWriting?
```

###### 参数

* **outlineView**

  开始拖拽的`Outline View`。

* **item**

  要返回一个`pasteboard writer`的`item`。

###### 返回值

一个实现了`NSPasteboardWriting`协议的自定义对象（或者直接使用`NSPasteboardItem`）。

###### 解释

如果这个方法被实现，那么[`outlineView(_:writeItems:to:)`](https://developer.apple.com/documentation/appkit/nsoutlineviewdatasource/1532910-outlineview)方法将不会被调用。



#### func outlineView(NSOutlineView, persistentObjectForItem: Any?)

`Outline View`调用这个方法来获取`item`对应的存档对象。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, persistentObjectForItem item: Any?) -> Any?
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。

* **item**

  需要返回存档对象的`item`。

###### 返回值

`item`的存档状态。如果这个`item`是一个存档对象，这个方法可以直接返回这个`item`。

###### 解释

当`Outline View`正在保存展开的`Items`时，这个方法会被每个展开的`Item`调用，将`Outline View`的`Item`转换为一个存档对象。

###### 特别注意事项

如果你设置为自动保存展开的`Items`（即[`autosaveExpandedItems`](https://developer.apple.com/documentation/appkit/nsoutlineview/1530638-autosaveexpandeditems)返回`true`时），那么你必须实现这个方法。



#### func outlineView(NSOutlineView, setObjectValue: Any?, for: NSTableColumn?, byItem: Any?)

设置在一个给定的列中给定的`Item`的数据对象。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, setObjectValue object: Any?, for tableColumn: NSTableColumn?, byItem item: Any?)
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。


* **object**

  `item`的新值。


* **tableColumn**

  `Outline View`中的一列。


* **item**

  视图中指定的`tableColumn`中的数据源中的一个`item`。

###### 解释

`item`位于视图中给定的`tableColumn`中。

> **重要**
>
> 虽然这个方法在协议中被标记为`@optional`，**如果你没有使用绑定数据给`Outline View`提供数据，那么你必须实现这个方法。**在这个方法中不要调用[`reloadData()`](https://developer.apple.com/documentation/appkit/nstableview/1528382-reloaddata)方法。



#### func outlineView(NSOutlineView, sortDescriptorsDidChange: [NSSortDescriptor])

被`Outline View`调用，用来通知数据源描述符改变，数据可能需要被重新排序。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, sortDescriptorsDidChange oldDescriptors: [NSSortDescriptor])
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。

* **oldDescriptors**

  一个包含了之前的描述符的数组。

###### 解释

数据源通常排序和重载数据，并相应的调整选择。如果数据源没有自己管理数据，并且你需要知道当前排序描述符，你可以给`Outline View`发送一个[`sortDescriptors`](https://developer.apple.com/documentation/appkit/nstableview/1534198-sortdescriptors)信息来获取当前排序描述符。



#### func outlineView(NSOutlineView, updateDraggingItemsForDrag: NSDraggingInfo)

实现这个方法，将允许表在拖动`Items`到视图上方时更新这些`Items`。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, updateDraggingItemsForDrag draggingInfo: NSDraggingInfo)
```

###### 参数

* **outlineView**

  拖动发生的`Outline View`。

* **draggingInfo**

  拖动信息对象。

###### 解释

多重图像拖动要求实现这个方法。一个典型的实现调用是通过拖动信息对象的[`enumerateDraggingItems(options:for:classes:searchOptions:using:)`](https://developer.apple.com/documentation/appkit/nsdragginginfo/1416074-enumeratedraggingitems)方法，设置拖动对象的[`imageComponentsProvider`](https://developer.apple.com/documentation/appkit/nsdraggingitem/1535607-imagecomponentsprovider)属性为一个基于内容的适当的图像。对于基于`NSView`的`Table View`，你可以使用`NSTableView`的[`draggingImageComponents`](https://developer.apple.com/documentation/appkit/nstablecellview/1483199-draggingimagecomponents)方法。



#### func outlineView(NSOutlineView, validateDrop: NSDraggingInfo, proposedItem: Any?, proposedChildIndex: Int)



Used by an outline view to determine a valid drop target.

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, validateDrop info: NSDraggingInfo, proposedItem item: Any?, proposedChildIndex index: Int) -> NSDragOperation
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。


* **info**

  一个包含了更多关于这个拖拽操作信息的对象。


* **item**

  建议的父级。


* **index**

  建议的子项索引值。

###### 返回值

一个值表示数据源是否将执行拖拽操作。

###### 解释

基于鼠标位置，`Outline View`将给一个建议拖拽位置。The data source may “retarget” a drop if desired by calling [`setDropItem(_:dropChildIndex:)`](https://developer.apple.com/documentation/appkit/nsoutlineview/1525351-setdropitem) and returning something other than `NSDragOperationNone`.  你可以因为各种原因选择重定位（例如，当插入一个排序的位置中时为了更好的视觉效果）。

这个方法的实现是可选的。



#### func outlineView(NSOutlineView, writeItems: [Any], to: NSPasteboard)

返回一个表示是否允许一个拖拽操作的布尔值。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, writeItems items: [Any], to pasteboard: NSPasteboard) -> Bool
```

###### 参数

* **outlineView**

  调用这个方法的`Outline View`。


* **items**

  一个参与拖动的`Items`数组。


* **pboard**

  将要写入拖拽数据的剪贴板。



## 关联

### 继承自

[`NSObjectProtocol`](https://developer.apple.com/documentation/objectivec/nsobjectprotocol)



## 参阅

### 管理

#### [protocol NSOutlineViewDelegate](./NSOutlineViewDelegate.md)

A set of optional methods implemented by delegates of [`NSOutlineView`](https://developer.apple.com/documentation/appkit/nsoutlineview) objects.