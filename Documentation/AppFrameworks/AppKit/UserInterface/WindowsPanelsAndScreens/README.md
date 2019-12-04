# `窗口`，`面板`和`屏幕`

整理你的视图层次结构，并方便其在屏幕上显示。

## 主题

### `窗口`

* [class NSWindow](./Windows/NSWindow.md)

App在屏幕上显示的窗口。

* [class NSPanel](./Windows/NSPanel.md)

一种特殊类型的`窗口`，通常执行`辅助窗口`的功能。

* [protocol NSWindowDelegate]()
A set of optional methods that a delegate of 
NSWindow
 can implement to respond to events, such as window resizing, moving, exposing, and minimizing.

* [class NSWindowTab]()
A tab associated with a window that is part of a tabbing group.

* [class NSWindowTabGroup]()
A group of windows that display together as a single tabbed window.

### 还原`窗口`

* [protocol NSWindowRestoration]()
A set of methods that restoration classes must implement to handle the recreation of windows.

* [protocol NSUserInterfaceItemIdentification]()
A set of methods used to associate a unique identifier with objects in your user interface.

### 屏幕

* [class NSScreen]()
An object that describes the attributes of a computer’s monitor or screen.

### `弹出式窗口`

* [class NSPopover](./Popovers/NSPopover.md)

一种在屏幕上显示与现有内容有关的其他内容的方法。

* [protocol NSPopoverDelegate]()
A set of optional methods that a popover delegate can implement to provide additional or custom functionality.

### `Alert`

* [class NSAlert]()
A modal dialog or sheet attached to a document window.

* [protocol NSAlertDelegate]()
A set of optional methods implemented by the delegate of an 
NSAlert
 object to respond to a user's request for help.

### 打开和保存面板

* [class NSOpenPanel]()
The Open panel for the Cocoa user interface.

* [class NSSavePanel]()
A Save panel that you can run in a modal loop.

* [protocol NSOpenSavePanelDelegate]()
A set of methods that a delegate of 
NSOpenPanel
 or 
NSSavePanel
 should implement.

### 打印和PDF面板

* [class NSPDFPanel]()
A Save or Export as PDF panel that’s consistent with the macOS user interface.

* [protocol NSPrintPanelAccessorizing]()
A set of methods that a print panel object can use to get information from a printing accessory controller.

### 颜色面板

* [class NSColorPanel]()
A standard user interface for selecting color in an app.

* [protocol NSColorPickingCustom]()
A set of methods that provides a way to add color pickers—custom user interfaces for color selection—to an app’s color panel.

* [protocol NSColorPickingDefault]()
A set of methods that provides basic behavior for a color picker.

* [class NSColorPicker]()
An abstract superclass that implements the 
NSColorPickingDefault
 protocol.

### 字体面板

* [class NSFontPanel]()
The Font panel—a user interface object that displays a list of available fonts, letting the user preview them and change the font used to display text.

* [struct NSFontPanel.ModeMask]()
NSFontPanelValidation
A set of methods you use to tell the Font panel to display some or all of its elements.

* [protocol NSFontChanging]()