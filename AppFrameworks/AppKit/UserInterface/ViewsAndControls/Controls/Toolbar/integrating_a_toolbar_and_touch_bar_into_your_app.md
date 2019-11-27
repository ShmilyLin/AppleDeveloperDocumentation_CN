# Integrating a Toolbar and Touch Bar into Your App

在应用程序窗口中构建带有相应Touchbar的Toolbar，以快速访问应用程序功能。

## 概述

[Toolbar]()管理窗口标题栏正下方和应用程序的自定义内容上方的空间。Toolbar管理应用于窗口内容的控件。

Toolbar中的每个Item均由[NSToolbarItem]()对象表示，该对象在Interface Builder中创建或以代码形式创建。此示例向你展示如何将Toolbar集成到`NSWindow`中。

### 创建Toolbar

通过将`NSToolbar`对象从Xcode的Library窗口拖动到你的`NSWindow`对象上，可以向Window中添加Toolbar。然后将Toolbar对象连接到Window Controller，并使其遵守[NSToolbarDelegate]()。

### 分配Toolbar Identifier

对于你创建的每个`NSToolbarItem`，必须为其分配一个类型为[NSToolbarItem.Identifier]()的唯一标识符。AppKit有几个已经定义好的内置Toolbar Item Identifier，用于云共享，打印以及显示字体和调色板。所有Toolbar Item都按照用户确定的顺序排列在Toolbar中，并且该顺序会自动保存为Toolbar配置的一部分。

此示例创建两个Identifier：一个用于设置字体大小，另一个用于设置`NSTextView`的字体样式。

```swift
private extension NSToolbarItem.Identifier {
    static let fontSize: NSToolbarItem.Identifier = NSToolbarItem.Identifier(rawValue: "FontSize")
    static let fontStyle: NSToolbarItem.Identifier = NSToolbarItem.Identifier(rawValue: "FontStyle")
}
```

### 创建被允许存在的Toolbar Item

将[toolbarAllowedItemIdentifiers(_:)]()作为必需函数实现，以返回Toolbar的Toolbar Item Identifier数组，并在配置面板中指定Item的内容和顺序。

```swift
func toolbarAllowedItemIdentifiers(_ toolbar: NSToolbar) -> [NSToolbarItem.Identifier] {
    return [ NSToolbarItem.Identifier.fontStyle,
             NSToolbarItem.Identifier.fontSize,
             NSToolbarItem.Identifier.space,
             NSToolbarItem.Identifier.flexibleSpace,
             NSToolbarItem.Identifier.print ]
}
```

### 创建默认的Toolbar Item

实现[toolbarDefaultItemIdentifiers(_:)]()以提供最初出现在工具栏中的默认Item集合。

```swift
func toolbarDefaultItemIdentifiers(_ toolbar: NSToolbar) -> [NSToolbarItem.Identifier] {
    return [.fontStyle, .fontSize]
}
```

### 依据一个Identifier创建一个Toolbar Item

作为Toolbar Delegate，你负责为定义的每个Identifier创建Toolbar Item。 在AppKit告诉你需要创建`NSToolbarItem`时，你应该基于Identifier创建一个。实现[toolbar(_:itemForItemIdentifier:willBeInsertedIntoToolbar:)]()以返回两个Toolbar Item：字体样式和字体大小。

```swift
func toolbar(
    _ toolbar: NSToolbar,
    itemForItemIdentifier itemIdentifier: NSToolbarItem.Identifier,
    willBeInsertedIntoToolbar flag: Bool) -> NSToolbarItem? {
    
    var toolbarItem: NSToolbarItem = NSToolbarItem()
    
    /**创建一个新的 NSToolbarItem，然后完成从 Master Toolbar Item 中设置与Item字典中的Identifier匹配的属性的过程。
     */
    if itemIdentifier == NSToolbarItem.Identifier.fontStyle {
        // 1) 字体样式 toolbar item.
        toolbarItem =
            customToolbarItem(itemForItemIdentifier: NSToolbarItem.Identifier.fontStyle.rawValue,
                              label: NSLocalizedString("Font Style", comment: ""),
                              paletteLabel: NSLocalizedString("Font Style", comment: ""),
                              toolTip: NSLocalizedString("tool tip font style", comment: ""),
                              itemContent: styleSegmentView)!
    } else if itemIdentifier == NSToolbarItem.Identifier.fontSize {
        // 2) 字体大小 toolbar item.
        toolbarItem =
            customToolbarItem(itemForItemIdentifier: NSToolbarItem.Identifier.fontSize.rawValue,
                              label: NSLocalizedString("Font Size", comment: ""),
                              paletteLabel: NSLocalizedString("Font Size", comment: ""),
                              toolTip: NSLocalizedString("tool tip font size", comment: ""),
                              itemContent: fontSizeView)!
    }
    
    return toolbarItem
}
```

每个Toolbar都有自己独特的Identifier集。如果Toolbar Item有自定义视图，则返回该Item时该View应已经准备好。不要假定将返回的Item添加为活动的Toolbar Item。实际上，Toolbar可能会在此处要求提供Item以构造自定义选项板（它制作了返回Item的副本）。 如果`willBeInsertedIntoToolbar`为`true`，则插入返回的项目，并最终调用`toolbarWillAddItem:`协议函数。

### 为Toolbar Item使用自定义View

将自定义View应用于`NSToolbarItem`时，将一个或多个控件放在一起代表该`NSToolbarItem`。在此示例中，包括的自定义View是字体样式的分段控件和字体大小控件，它们由标签，步进器和编辑字段组成。

### 为Toolbar Item添加更多属性

使用可选的[toolbarWillAddItem(_:)]()协议函数。当新Item要添加到Toolbar时，将调用此函数。目前，你可以添加或更改Toolbar Item的初始状态信息，尤其是你不直接控制的Toolbar Item，例如`NSToolbarPrintItemIdentifier`。在此示例中，你将工具提示字符串添加到Print Toolbar Item。

### 自定义Toolbar

你可以实现协议函数`toolbarAllowedItemIdentifiers`，以确定用户在Toolbar中放置的Toolbar Item。用户可以通过右键单击Toolbar或从“View”菜单中选择“Customize Toolbar”来自定义Item顺序。此选项将打开一个定制弹窗，用户可以在其中更改布局。该弹窗中仅显示协议函数`toolbarAllowedItemIdentifiers`返回的Item。

### 添加Touch Bar支持

