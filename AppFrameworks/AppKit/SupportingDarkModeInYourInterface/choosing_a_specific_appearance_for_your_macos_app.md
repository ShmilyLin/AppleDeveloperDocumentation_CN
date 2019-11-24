# Choosing a Specific Appearance for Your macOS App

当不适合同时支持浅色和深色模式时，请为你的Window，View或应用程序采用特定的外观。

## 概述

同时支持浅色和深色外观都是不错的做法，但是你可能有充分的理由选择完全或部分退出应用程序中的外观更改。包含用户创建的内容的视图应始终反映用户的选择。同样，你可以为与打印相关的视图选择特定的外观，以便它们反映用户在打印页面上看到的内容。

系统假定与macOS 10.14或更高版本的SDK链接的应用程序既支持浅色外观，也支持深色外观。你可以为Window，View和Popover View分配特定外观。你也可以使用`Info.plist`的Key完全禁用对深色模式的支持。

有关如何支持深色模式的一般信息，请参见[在界面中支持深色模式](./)。

## 为View或Window分配特定外观

当你希望AppKit的View或Window采用特定外观时，请为其分配自定义的[NSAppearance]()对象。通常，你的应用程序对象继承系统外观，并将该外观传播到所有View和Panel，而View则从其Super View或Window继承外观。如果在此链中的不同点上为对象分配了特定外观，则所有子对象都将继承新外观。例如，如果将新外观分配给Window，则该Window及其所有View都将继承该外观。

要将特定外观分配给Storyboard文件中的View或Window，请在检查器中更改`appearance`属性，如下图所示。

![./909bc4b8-02ac-4f1d-84ce-ed62aa25601f.png]()

要以编程方式进行相同的更改，请将适当的[NSAppearance]()对象分配给Window或View的[appearance]()属性。以下示例代码显示了一种将Aqua外观分配给View的方法。View的每个初始化方法都必须调用此方法。

```swift
class MyContentView : NSView {

  func adoptAquaAppearance()
      self.appearance = NSAppearance(named: .aqua)
   }

}
```

### 为你的应用分配特定外观

要为整个应用程序采用特定外观，请为[NSApplication]()对象的[appearance]()属性分配一个值。仅在你的设计需要时选择应用程序范围的外观。例如，照片编辑应用程序可能始终使用深色外观，以便用户可以专注于自己的照片，而不是应用程序的边框。以下代码示例显示了如何为应用分配深色外观。

```swift
NSApp.appearance = NSAppearance(named: .darkAqua)
```

### 选择退出深色模式

系统会自动在与macOS 10.14或更高版本的SDK链接的任何应用中选择浅色外观和深色外观。如果你需要更多时间来处理应用程序的深色模式支持，可以通过在应用程序的`Info.plist`文件中包含`NSRequiresAquaSystemAppearance`的Key（值为`true`）来表示暂时不支持深色模式。将此Key设置为`true`会导致系统忽略用户的首选项，并始终将你的应用程序设置为浅色外观。

> **重要**
> 
> 强烈建议支持深色模式。仅在对应用程序的深色模式支持进行改进时，才可以使用`NSRequiresAquaSystemAppearance`的Key来表示暂时不支持深色模式。如果你根本不打算支持深色外观，请按照[为你的应用分配特定外观]()中所述，将浅色外观应用于整个应用程序。

如果你使用较早的SDK构建应用程序，但仍希望支持深色模式，请在应用程序的`Info.plist`文件中包含`NSRequiresAquaSystemAppearance`的Key（值为`false`）。仅当在macOS 10.14及更高版本中启用了深色模式的应用程序的外观看起来正确时，才执行此操作。
