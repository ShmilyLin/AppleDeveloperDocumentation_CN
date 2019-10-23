# NSTableColumn

显示一个`Table View`中一个列的性质和标示。



## 概述

一个`Table Column`对象决定了它的列在`Table View`中的宽度，以及指定列的调整大小和编辑的行为事件。一个`Table Column`存储两个`Cell`对象：被绘制在列的头部的`Header Cell`，和被绘制每一行的`Data Cell`。在一个基于`Cell`的表中，你可以通过使用给定`NSCell`的子类来控制列的显示，以及通过设置字体和其他显示性质来控制这些`Cells`的显示。例如，你可以使用一个[`NSTextFieldCell`](apple-reference-documentation://hsXqahhn8m)类展示字符串，或者使用一个[`NSImageCell`](apple-reference-documentation://hs8615vwof)展示图片。



## 讲解

### 创建一个`Table Column`

#### init(identifier: NSUserInterfaceItemIdentifier)

使用一个字符串标示创建并初始化一个新的`Table Column`。

###### 声明

```swift
init(identifier: NSUserInterfaceItemIdentifier)
```

###### 参数

`identifier`

The string identifier for the column.



---

### 设置`Table View`

#### var tableView: NSTableView?

The table view that contains the table column.



---

### 控制大小

#### var width: CGFloat

The table column’s width, in points.

#### var minWidth: CGFloat

The table column’s minimum width, in points.

#### var maxWidth: CGFloat

The table column’s maximum width, in points.

#### var resizingMask: NSTableColumn.ResizingOptions

The table column’s resizing mask.

#### func sizeToFit()

Resizes the table column to fit the width of its header cell.



---

### Setting the Header

```
var title: String
```

The title of the table column’s header.

```
var headerCell: NSTableHeaderCell
```

The cell used to draw the table column’s header.

### Setting the Identifier

```
var identifier: NSUserInterfaceItemIdentifier
```

The identifier string for the table column.

### Controlling Editability in a Cell-Based Table

```
var isEditable: Bool
```

A Boolean that indicates whether a cell-based table’s column cells are user editable.

### Sorting

```
var sortDescriptorPrototype: NSSortDescriptor?
```

The table column’s sort descriptor prototype.

### Setting Column Visibility

```
var isHidden: Bool
```

A Boolean that indicates whether the table column is hidden.

### Setting Tooltips

```
var headerToolTip: String?
```

The string that’s displayed in a help tag over the table column header.

### Deprecated Methods

```
var dataCell: Any
```

The cell prototype used by the table column to draw individual cells.

Deprecated

```
func dataCell(forRow: Int)
```

Returns the cell object used to display values in the specified row of the table column.

Deprecated

### Initializers

`init(coder: NSCoder)`

### Structures

`struct NSTableColumn.ResizingOptions`

## Relationships

### Inherits From

[`NSObject`](apple-reference-documentation://hsttKQiP8Q)

### Conforms To

- [`CVarArg`](apple-reference-documentation://hs16nXL9Fo)
- [`Equatable`](apple-reference-documentation://hs-MXxh1WG)
- [`Hashable`](apple-reference-documentation://hsx4S2g0iZ)
- [`NSCoding`](apple-reference-documentation://hsUvGdfQOR)
- [`NSUserInterfaceItemIdentification`](apple-reference-documentation://hs2qrbMvbK)