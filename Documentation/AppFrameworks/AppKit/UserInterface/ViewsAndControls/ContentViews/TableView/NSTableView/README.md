# NSTableView

一组相关记录，显示在代表各个记录的行中和代表这些记录的属性的列中。

## 定义

```swift
class NSTableView : NSControl
```

## 概述

`表格视图`以`滚动视图`显示。从macOS v10.7开始，你可以使用`NSView`对象（最常用的自定义[NSTableCellView]()对象）代替用于指定行和列的`单元格`。如果愿意，你仍可以为每个行和列项使用[NSCell]()对象。

`表格视图`不存储自己的数据；它会根据需要从具有弱引用的数据源中检索数据值。因此，不应在`表格视图`中以编程方式直接设置数据值。而是，修改数据源中的值，并使更改反映在`表格视图`中。要了解`NSTableView`对象用于提供和访问其数据源对象内容的方法，请参见[NSTableViewDataSource]()。

要自定义`表格视图`的行为而不将其归类为`NSTableView`，请使用[NSTableViewDelegate]()协议定义的方法。例如，委托支持表列管理，类型选择功能，行选择和编辑，自定义跟踪以及各个列和行的自定义视图。要了解有关`表格视图`委托的更多信息，请参见[NSTableViewDelegate]()。

> **重要**
> 
> 如果在`Interface Builder`中指定了数据源，则可能会在调用[awakeFromNib()]()之前调用用于填充`表格视图`的数据源方法。你应该通过在尚未配置数据源的情况下使数据源的[numberOfRows(in:)]()方法返回`0`作为行数来对此进行防御。在[awakeFromNib()]()中，初始化数据源时，应始终在`表格视图`上调用[reloadData]()。

### 子类化

通常不需要子类化`NSTableView`。而是使用委托对象（符合[NSTableViewDelegate]()协议的对象）和数据源对象（符合[NSTableViewDataSource]()协议）或通过子类化以下子组件之一来自定义`表格视图`：单元格（使用基于[NSCell]()的表时），行单元格视图或行视图（使用基于[NSView]()的表视图时），表格列类或表格列标题类。

## 主题

### 创建一个表格

init?(coder: NSCoder)
init(frame: NSRect)

### 管理表格的数据

var dataSource: NSTableViewDataSource?
The object that provides the data displayed by the table view.

* [var usesStaticContents: Bool](./1533450-usesstaticcontents.md)

    一个布尔值，指示表格是否使用静态数据。

func reloadData()
Marks the table view as needing redisplay, so it will reload the data for visible cells and draw the new values.

func reloadData(forRowIndexes: IndexSet, columnIndexes: IndexSet)
Reloads the data for only the specified rows and columns.

### 创建显示的视图

* [func makeView(withIdentifier: NSUserInterfaceItemIdentifier, owner: Any?) -> NSView?](./1535482-makeview.md)

    返回具有指定标识符的新视图或现有视图。

* [func rowView(atRow: Int, makeIfNecessary: Bool) -> NSTableRowView?](./1525162-rowview.md)

    返回指定索引处的行视图，必要时创建一个。

* [func view(atColumn: Int, row: Int, makeIfNecessary: Bool) -> NSView?](./1528831-view.md)

    在指定的行和列索引处返回一个视图，并在必要时创建一个视图。

struct NSUserInterfaceItemIdentifier

### 更新表格视图的排列

func beginUpdates()
Begins a group of updates for the table view.

func endUpdates()
Ends the group of updates for the table view.

func moveRow(at: Int, to: Int)
Moves the specified row to the new row location using animation.

func insertRows(at: IndexSet, withAnimation: NSTableView.AnimationOptions)
Inserts the rows using the specified animation.

func removeRows(at: IndexSet, withAnimation: NSTableView.AnimationOptions)
Removes the rows using the specified animation.

func row(for: NSView) -> Int
Returns the index of the row for the specified view.

func column(for: NSView) -> Int
Returns the column index for the specified view.

### 基于`NSView`的表格的`nib`文件注册

* [func register(NSNib?, forIdentifier: NSUserInterfaceItemIdentifier)](./1524297-register.md)

    为指定的标识符注册`NIB`，以便基于视图的表格视图可以使用它来实例化视图。

* [var registeredNibsByIdentifier: [NSUserInterfaceItemIdentifier : NSNib]?](./1530663-registerednibsbyidentifier.md)

    获取基于视图的表格视图的所有已注册的标识符对应的`nib`文件的字典。

### `Target-Action`行为

var doubleAction: Selector?
The message sent to the table view’s target when the user double-clicks a cell or column header.

var clickedColumn: Int
The index of the column the user clicked.

var clickedRow: Int
The index of the row the user clicked.

### 配置行为

* [var allowsColumnReordering: Bool]()

    一个布尔值，指示`表格视图`是否允许用户通过拖动标题来重新排列`列`。

* [var allowsColumnResizing: Bool]()

    一个布尔值，指示`表格视图`是否允许用户通过在标题之间拖动来调整`列`的大小。

* [var allowsMultipleSelection: Bool]()

    一个布尔值，指示`表格视图`是否允许用户一次选择多个`列`或`行`。

* [var allowsEmptySelection: Bool]()

    一个布尔值，指示`表格视图`是否允许用户选择零`列`或零`行`。

* [var allowsColumnSelection: Bool]()

    一个布尔值，指示`表格视图`是否允许用户通过单击列标题来选择`列`。

* [var usesAutomaticRowHeights: Bool]()

### 设置显示属性

* [var intercellSpacing: NSSize](./1524258-intercellspacing.md)

    `单元格`之间的水平和垂直间距。

* [var rowHeight: CGFloat](./1529148-rowheight.md)

    表格中每一行的高度。

* [var backgroundColor: NSColor](./1527806-backgroundcolor.md)

    用于绘制表格背景的颜色。

* [var usesAlternatingRowBackgroundColors: Bool](./1533967-usesalternatingrowbackgroundcolo.md)

    一个布尔值，指示`表格视图`是否为其背景使用交替的行颜色。

* [var selectionHighlightStyle: NSTableView.SelectionHighlightStyle]()

    `表格视图`用于指示行和列选择的选择突出显示样式。

* [var gridColor: NSColor](./1524620-gridcolor.md)

    用于绘制网格线的颜色。

* [var gridStyleMask: NSTableView.GridLineStyle](./1528689-gridstylemask.md)

    `表格视图`绘制的网格线。

* [func indicatorImage(in: NSTableColumn) -> NSImage?](./1524846-indicatorimage.md)

    返回指定`列`的指示符图像。

* [func setIndicatorImage(NSImage?, in: NSTableColumn)](./1534381-setindicatorimage.md)

    设置指定`列`的指示符图像。

### 获取和设置行尺寸的样式

* [var effectiveRowSizeStyle: NSTableView.RowSizeStyle](./1531825-effectiverowsizestyle.md)

    表格的有效`行`的大小样式。

* [var rowSizeStyle: NSTableView.RowSizeStyle](./1534438-rowsizestyle.md)

    `表格视图`使用的`行`的大小样式（小，中，大或自定义）。

### 管理列

func addTableColumn(NSTableColumn)
Adds the specified column as the last column of the table view.

func removeTableColumn(NSTableColumn)
Removes the specified column from the table view.

func moveColumn(Int, toColumn: Int)
Moves the column and heading at the specified index to the new specified index.

var tableColumns: [NSTableColumn]
An array containing the current table column objects.

func column(withIdentifier: NSUserInterfaceItemIdentifier) -> Int
Returns the index of the first column in the table view whose identifier is equal to the specified identifier.

func tableColumn(withIdentifier: NSUserInterfaceItemIdentifier) -> NSTableColumn?
Returns the NSTableColumn object for the first column whose identifier is equal to the specified object.

### 选中列和行

func selectColumnIndexes(IndexSet, byExtendingSelection: Bool)
Sets the column selection using indexes possibly extending the selection.

var selectedColumn: Int
The index of the last selected column (or the last column added to the selection).

var selectedColumnIndexes: IndexSet
An index set containing the indexes of the selected columns.

func deselectColumn(Int)
Deselects the column at the specified index if it’s selected.

var numberOfSelectedColumns: Int
The number of selected columns.

func isColumnSelected(Int) -> Bool
Returns a Boolean value that indicates whether the column at the specified index is selected.

func selectRowIndexes(IndexSet, byExtendingSelection: Bool)
Sets the row selection using indexes extending the selection if specified.

var selectedRow: Int
The index of the last selected row (or the last row added to the selection).

var selectedRowIndexes: IndexSet
An index set containing the indexes of the selected rows.

func deselectRow(Int)
Deselects the row at the specified index if it’s selected.

var numberOfSelectedRows: Int
The number of selected rows.

func isRowSelected(Int) -> Bool
Returns a Boolean value that indicates whether the row at the specified index is selected.

func selectAll(Any?)
Selects all rows or all columns, according to whether rows or columns were most recently selected.

func deselectAll(Any?)
Deselects all selected rows or columns if empty selection is allowed; otherwise does nothing.

### 枚举表格的行

func enumerateAvailableRowViews((NSTableRowView, Int) -> Void)
Allows the enumeration of all the table rows that are known to the table view.

### 管理类型选择

* [var allowsTypeSelect: Bool](./1526084-allowstypeselect.md)

    一个布尔值，指示`表格视图`是否允许用户键入字符以选择行。

### 表格纬度

* [var numberOfColumns: Int](./1528902-numberofcolumns.md)

    表格的列数。

* [var numberOfRows: Int](./1527941-numberofrows.md)

    表格的行数。

### 获取和设置浮动行

* [var floatsGroupRows: Bool]()
A Boolean value indicating whether the table view draws grouped rows as if they are floating.

### 编辑单元格

* [func editColumn(Int, row: Int, with: NSEvent?, select: Bool)]()
Edits the cell at the specified column and row using the specified event and selection behavior.

* [var editedColumn: Int]()
The index of the column being edited.

* [var editedRow: Int]()
The index of the row being edited.

### 添加和删除行视图

* [func didAdd(NSTableRowView, forRow: Int)]()
Invoked when a row view is added to the table.

* [func didRemove(NSTableRowView, forRow: Int)]()
Invoked when a row view is removed from the table.

### 设置辅助视图

* [var headerView: NSTableHeaderView?]()
The view object used to draw headers over columns.

* [var cornerView: NSView?]()
The view used to draw the area to the right of the column headers and above the vertical scroller of the enclosing scroll view.

### 约束支持

var userInterfaceLayoutDirection: NSUserInterfaceLayoutDirection
The layout direction of the user interface.

func rect(ofColumn: Int) -> NSRect
Returns the rectangle containing the column at the specified index.

func rect(ofRow: Int) -> NSRect
Returns the rectangle containing the row at the specified index.

func rows(in: NSRect) -> NSRange
Returns a range of indexes for the rows that lie wholly or partially within the vertical boundaries of the specified rectangle.

func columnIndexes(in: NSRect) -> IndexSet
Returns the indexes of the table view’s columns that intersect the specified rectangle.

func column(at: NSPoint) -> Int
Returns the index of the column the specified point lies in.

func row(at: NSPoint) -> Int
Returns the index of the row the specified point lies in.

func frameOfCell(atColumn: Int, row: Int) -> NSRect
Returns a rectangle locating the cell that lies at the intersection of the specified column and row.

var columnAutoresizingStyle: NSTableView.ColumnAutoresizingStyle
The table view’s column autoresizing style.

func sizeLastColumnToFit()
Resizes the last column so the table view fits exactly within its enclosing clip view.

func noteNumberOfRowsChanged()
Informs the table view that the number of records in its data source has changed.

func tile()
Properly sizes the table view and its header view and marks it as needing display.

func sizeToFit()
Sizes the table view based on a uniform column autoresizing style.

func noteHeightOfRows(withIndexesChanged: IndexSet)
Informs the table view that the rows specified in indexSet have changed height.

### 绘制

* [func drawRow(Int, clipRect: NSRect)]()
Draws the cells for the row at rowIndex in the columns that intersect clipRect.

* [func drawGrid(inClipRect: NSRect)]()
Draws the grid lines within the supplied rectangle.

* [func highlightSelection(inClipRect: NSRect)]()
Highlights the region of the table view in the specified rectangle.

* [func drawBackground(inClipRect: NSRect)]()
Draws the background of the table view in the clip rect specified by the rectangle.

### 滚动

* [func scrollRowToVisible(Int)]()
Scrolls the view so the specified row is visible.

* [func scrollColumnToVisible(Int)]()
Scrolls the view so the specified column is visible.

### 表格列状态持久性

var autosaveTableColumns: Bool
A Boolean value indicating whether the order and width of the table view’s columns are automatically saved.

var autosaveName: NSTableView.AutosaveName?
The name under which table information is automatically saved.

typealias NSTableView.AutosaveName

### 访问代理

var delegate: NSTableViewDelegate?
The table view’s delegate.

### 表格列标题的突出显示

var highlightedTableColumn: NSTableColumn?
The column highlighted in the table.

### 拖拽

* [func dragImageForRows(with: IndexSet, tableColumns: [NSTableColumn], event: NSEvent, offset: NSPointPointer) -> NSImage]()
Computes and returns an image to use for dragging.

* [func canDragRows(with: IndexSet, at: NSPoint) -> Bool]()
Returns a Boolean value indicating whether the table view allows dragging the rows with the drag initiated at the specified point.

* [func setDraggingSourceOperationMask(NSDragOperation, forLocal: Bool)]()
Sets the default operation mask returned by draggingSourceOperationMaskForLocal: to mask.

* [var verticalMotionCanBeginDrag: Bool]()
A Boolean value indicating whether vertical motion is treated as a drag or selection change.

* [var draggingDestinationFeedbackStyle: NSTableView.DraggingDestinationFeedbackStyle]()
The feedback style displayed when the user drags over the table view.

* [func setDropRow(Int, dropOperation: NSTableView.DropOperation)]()
Retargets the proposed drop operation.

### 排序

* [var sortDescriptors: [NSSortDescriptor]]()
The table view’s sort descriptors.

### 行动作

* [var rowActionsVisible: Bool]()
A Boolean value indicating whether a table row’s actions are visible.

### 隐藏和显示表格的行

* [func hideRows(at: IndexSet, withAnimation: NSTableView.AnimationOptions)]()
Hides the specified table rows.

* [func unhideRows(at: IndexSet, withAnimation: NSTableView.AnimationOptions)]()
Unhides the specified table rows.

* [var hiddenRowIndexes: IndexSet]()
The indexes of all hidden table rows.

### 常量

Specifying a Custom Row View in a Nib File
View-based table view instances use NSTableViewRowKey to identify the nib file containing the template row view. You can specify a custom row view (without any code) by associating this key with the appropriate nib name in Interface Builder.

enum NSTableView.DraggingDestinationFeedbackStyle
These constants specify the drag styles displayed by the table view. They’re used by 
draggingDestinationFeedbackStyle
.

enum NSTableView.DropOperation
NSTableView defines these constants to specify drop operations.

struct NSTableView.GridLineStyle
NSTableView defines these constants to specify grid styles. These constants are used by the 
gridStyleMask
 property. The mask can be either 
gridNone
 or it can contain either or both of the other options combined using the C bitwise OR operator.

enum NSTableView.ColumnAutoresizingStyle
The following constants specify the autoresizing styles. These constants are used by the 
columnAutoresizingStyle
 property.

enum NSTableView.SelectionHighlightStyle
The following constants specify the selection highlight styles. These constants are used by the 
selectionHighlightStyle
 property.

struct NSTableView.AnimationOptions
Specifies the animation effects to apply when inserting or removing rows.

enum NSTableView.RowSizeStyle
The row size style constants define the size of the rows in the table view. They are used by the 
effectiveRowSizeStyle
 and 
rowSizeStyle
 properties. You can also query the row size in the 
NSTableCellView
 class’ property 
rowSizeStyle
.

enum NSTableView.RowActionEdge
These constants define table row edges on which row actions are attached. They are used by the tableView:rowActionsForRow:edge: delegate method.

### 通知

class let columnDidMoveNotification: NSNotification.Name
Posted whenever a column is moved by user action in an NSTableView object.

class let columnDidResizeNotification: NSNotification.Name
Posted whenever a column is resized in an NSTableView object.

class let selectionDidChangeNotification: NSNotification.Name
Posted after an NSTableView object's selection changes.

class let selectionIsChangingNotification: NSNotification.Name
Posted as an NSTableView object's selection changes (while the mouse button is still down).