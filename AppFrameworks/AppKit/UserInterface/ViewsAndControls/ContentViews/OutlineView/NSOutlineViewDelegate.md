# NSOutlineViewDelegate

[`NSOutlineView`](./NSOutlineView.md)对象协议的一组可选实现的方法。



## 讲解

### 展开和折叠`Outline View`

#### func outlineView(NSOutlineView, shouldExpandItem: Any)

`Outline View`是否需要展开一个给定的`Item`。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, shouldExpandItem item: Any) -> Bool
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。

* **item**

  需要被展开的`Item`。

###### 返回值

`true`表示允许`Outline View`展开`item`，`false`则表示不允许。

###### 解释

`delegate`可以实现这个方法来禁止指定的`Items`展开。



#### func outlineView(NSOutlineView, shouldCollapseItem: Any)

`Outline View`是否需要折叠一个给定的`Item`。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, shouldCollapseItem item: Any) -> Bool
```

###### 参数

- **outlineView**

  发送消息的`Outline View`。

- **item**

  需要被折叠的`Item`。

###### 返回值

`true`表示允许`Outline View`折叠`item`，`false`则表示不允许。

###### 解释

`delegate`可以实现这个方法来禁止指定的`Items`折叠。例如，如果你的`Outline View`的第一行需要不可以被折叠，你的`delegate`方法可以包含下面这行代码：

```swift
return [outlineView rowForItem:item]!=0;
```



---

### 支持选择类型

#### func outlineView(NSOutlineView, typeSelectStringFor: NSTableColumn?, item: Any)

返回给定的列和`Item`的选择类型。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, typeSelectStringFor tableColumn: NSTableColumn?, item: Any) -> String?
```

###### 参数

- **outlineView**

  发送消息的`Outline View`。

- **tableColumn**

  `Outline View`中的一列。

- **item**

  `Outline View`中的一个`Item`。

###### 返回值

被用于指定选择类型的字符串。你可能想要根据基于显示的内容搜索出来的内容作出改变，或者如果行和／或列不允许搜索则直接返回`nil`。

###### 解释

如果你想要控制被用来指定选择类型的字符串的话就实现这个方法。You may want to change what is searched for based on what is displayed, or simply return `nil` to specify that the given row and/or column should not be searched. 默认的，所有`cells`中带有文本的都可以被搜索。

如果没有实现这个方法，那么默认值是：

```swift
[[outlineView preparedCellAtColumn:tableColumn row:[outlineView rowForItem:item]] stringValue]
```

如果你愿意，你可以在`delegate`的这个方法中返回这个值。



#### func outlineView(NSOutlineView, nextTypeSelectMatchFromItem: Any, toItem: Any, for: String)



Returns the first item that matches the searchString from within the range of startItem to endItem



#### func outlineView(NSOutlineView, shouldTypeSelectFor: NSEvent, withCurrentSearch: String?)



Returns a Boolean value that indicates whether type select should proceed for a given event and search string.



---

### 工具提示

#### func outlineView(NSOutlineView, toolTipFor: NSCell, rect: NSRectPointer, tableColumn: NSTableColumn?, item: Any, mouseLocation: NSPoint)



When the cursor pauses over a given cell, the value returned from this method is displayed in a tooltip.



---

### 处理选择

#### func outlineView(NSOutlineView, shouldSelect: NSTableColumn?) 



Returns a Boolean value that indicates whether the outline view should select a given table column.



#### func outlineView(NSOutlineView, shouldSelectItem: Any)

Returns a Boolean value that indicates whether the outline view should select a given item.



#### func outlineView(NSOutlineView, selectionIndexesForProposedSelection: IndexSet)

Invoked to allow the delegate to modify the proposed selection.



#### func selectionShouldChange(in: NSOutlineView)

Returns a Boolean value that indicates whether the outline view should change its selection.



#### func outlineViewSelectionIsChanging(Notification)

Invoked when `notification` is posted—that is, whenever the outline view’s selection changes.



#### func outlineViewSelectionDidChange(Notification)

Invoked when the selection did change notification is posted—that is, immediately after the outline view’s selection has changed.



---

### 展示`Cells`

#### func outlineView(NSOutlineView, willDisplayCell: Any, for: NSTableColumn?, item: Any)

通知`delegate`，给定的列中的`cell`将要被展示。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, willDisplayCell cell: Any, for tableColumn: NSTableColumn?, item: Any)
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。


* **cell**

  The cell.


* **tableColumn**

  The table column.


* **item**

  The item.

###### 解释

`delegate`可以实现这个方法修改`cell`来给 `tableColumn`和`item`中的`cell`提供更深层次的设置。在这个方法中绘图是不安全的——在这里你只能设置`cell`的状态。



#### func outlineView(NSOutlineView, willDisplayOutlineCell: Any, for: NSTableColumn?, item: Any)

通知`delegate`，`Outline View`即将显示一个用于绘制扩展符号的`cell`。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, willDisplayOutlineCell cell: Any, for tableColumn: NSTableColumn?, item: Any)
```

###### 参数

- **outlineView**

  发送消息的`Outline View`。


- **cell**

  The cell.


- **tableColumn**

  The table column.


- **item**

  The item.

###### 解释

通知`delegate`，`Outline View`即将显示一个`cell`——一个可以展开的`Cell`（即包含了展开符号的`Cell`）——对应了通过`tableColumn`和`item`给定的列和项。`delegate`可以修改`cell`将要显示的特性。

当`Outline View`将要显示一个不可以被展开的`cell`的时候，这个方法将不会被触发。



#### func outlineView(NSOutlineView, dataCellFor: NSTableColumn?, item: Any)

返回一个给定的列和项中要被使用的`cell`。

###### 声明

```swift
optional func outlineView(_ outlineView: NSOutlineView, dataCellFor tableColumn: NSTableColumn?, item: Any) -> NSCell?
```

###### 参数

* **outlineView**

  发送消息的`Outline View`。


* **tableColumn**

  需要`cell`的`tableColumn`。这个值可能为`nil`。


* **item**

  需要`cell`的`item`。

###### 返回值

The cell to use in column `tableColumn` for item `item`, or `nil`. The cell must properly implement `copyWithZone:` (since it may be copied by by the outline view).



#### func outlineView(NSOutlineView, shouldShowOutlineCellForItem: Any)

Returns whether the specified item should display the outline cell (the disclosure triangle).



#### func outlineView(NSOutlineView, shouldShowCellExpansionFor: NSTableColumn?, item: Any)

Invoked to allow the delegate to control cell expansion for a specific column and item.



---

### 移动列以及调整列的大小

#### func outlineView(NSOutlineView, shouldReorderColumn: Int, toColumn: Int)

Sent to the delegate to allow or prohibit the specified column to be dragged to a new location.



---

### Working with the Outline Column

#### func outlineViewColumnDidMove(Notification)

Invoked whenever the user moves a column in the outline view.



#### func outlineViewColumnDidResize(Notification)

Invoked whenever the user resizes a column in the outline view.



#### func outlineViewItemWillExpand(Notification)

Invoked when `notification` is posted—that is, whenever the user is about to expand an item in the outline view.



#### func outlineViewItemDidExpand(Notification)

Invoked when `notification` is posted—that is, whenever the user expands an item in the outline view.



#### func outlineViewItemWillCollapse(Notification)

Invoked when `notification` is posted—that is, whenever the user is about to collapse an item in the outline view.



#### func outlineViewItemDidCollapse(Notification)

Invoked when the did collapse notification is posted—that is, whenever the user collapses an item in the outline view.



---

### 编辑`Items`

#### func outlineView(NSOutlineView, shouldEdit: NSTableColumn?, item: Any)

Returns a Boolean value that indicates whether the outline view should allow editing of a given item in a given table column.



---

### Working with Table Columns

#### func outlineView(NSOutlineView, mouseDownInHeaderOf: NSTableColumn)

Sent to the delegate whenever the mouse button is clicked in `outlineView` while the cursor is in a column header `tableColumn`.



#### func outlineView(NSOutlineView, didClick: NSTableColumn)

Sent at the time the mouse button subsequently goes up in `outlineView` and `tableColumn` has been “clicked” without having been dragged anywhere.



#### func outlineView(NSOutlineView, didDrag: NSTableColumn)

Sent at the time the mouse button goes up in `outlineView` and `tableColumn` has been dragged during the time the mouse button was down.



---

### 自定义列和行的大小

#### func outlineView(NSOutlineView, heightOfRowByItem: Any)`

Returns the height in points of the row containing `item`.



#### func outlineView(NSOutlineView, sizeToFitWidthOfColumn: Int)`

Invoked to allow the delegate to provide custom sizing behavior when a column’s resize divider is double clicked.



---

### Customizing Tracking Support

#### func outlineView(NSOutlineView, shouldTrackCell: NSCell, for: NSTableColumn?, item: Any)

Returns a Boolean value that indicates whether a given cell should be tracked.



---

### Grouping Rows

#### func outlineView(NSOutlineView, isGroupItem: Any)

Returns a Boolean that indicates whether a given row should be drawn in the “group row” style.



---

### Working with NSView-Based Outline Views

#### func outlineView(NSOutlineView, didAdd: NSTableRowView, forRow: Int)`

Implemented to know when a new row view is added to the table.



#### func outlineView(NSOutlineView, didRemove: NSTableRowView, forRow: Int)`

Implemented to know when a row view is removed from the table



#### func outlineView(NSOutlineView, rowViewForItem: Any)`

implement this method to return a custom `NSTableRowView` for a particular item.



#### func outlineView(NSOutlineView, viewFor: NSTableColumn?, item: Any)`

Implemented to return the view used to display the specified item and column.



## 关联

### 继承自

[`NSControlTextEditingDelegate`](https://developer.apple.com/documentation/appkit/nscontroltexteditingdelegate)



## See Also

### Management

`protocol NSOutlineViewDataSource`

A set of methods that an outline view calls to retrieve data and information about it from the data source delegate, and—optionally—to update data values.