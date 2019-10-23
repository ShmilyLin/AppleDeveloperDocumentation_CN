# UIInputViewController

一个自定义键盘应用程序扩展的主视图控制器。

> iOS 8.0+
> tvOS 9.0+

## 概述

要创建一个自定义键盘，首先创建`UIInputViewController`类的子类，然后将你的键盘的用户界面添加到这个子类的[inputView]()属性中。在Xcode中，您可以通过选择`Custom Keyboard`的 target 模板来开始自定义键盘。

自定义键盘可以通过以下方式响应用户输入事件：

* 在当前文本输入对象的插入点，通过调用[textDocumentProxy]()属性的[insertText(_:)]()方法，插入一个非富文本格式的[NSString]()对象文本.该属性通过遵守[UIKeyInput]()协议来提供该方法。
* 通过调用[textDocumentProxy]()属性的[deleteBackward()]()方法，从插入点开始反向删除文本。
* 通过调用[advanceToNextInputMode()]()方法，切换到用户已启用的所有键盘中的另一个键盘。
* 通过调用[dismissKeyboard()]()方法关闭键盘。

通过阅读[textDocumentProxy]()属性的[documentContextBeforeInput]()和[documentContextAfterInput]()获取插入点周围的文本上下文。要确定当前文本输入对象是否为空，请调用[textDocumentProxy]()属性上的[hasText]()方法。通过将其与用户输入一起考虑，您可以使用此文本上下文，从键盘向文档提供上下文相关输出。

输入视图控制器符合UITextInputDelegate协议，允许您响应文档内容和插入点位置的更改。

要呈现适当的键盘布局，请响应当前文本输入对象的UIKeyboardType属性。 对于您支持的每种键盘类型特征，相应地更改主视图的内容。

有关创建自定义键盘的更多信息，请参阅应用程序扩展编程指南中的自定义键盘

Obtain textual context around the insertion point by reading the textDocumentProxy properties documentContextBeforeInput and documentContextAfterInput. To find out if the current text input object is empty, call the  method on the textDocumentProxy property. You can employ this textual context by considering it along with user input, to offer context-sensitive output to a document from your keyboard.

An input view controller conforms to the UITextInputDelegate protocol, allowing you to respond to changes in document content and position of the insertion point.

To present an appropriate keyboard layout, respond to the current text input object’s UIKeyboardType property. For each keyboard type trait you support, change the contents of your primary view accordingly.

For more about creating a custom keyboard, read Custom Keyboard in App Extension Programming Guide.

---
## 专题

### 一、自定义键盘提供用户界面

#### ● [var inputView: UIInputView?]()

UIInputViewController的主视图（the primary view）。

### 二、控制自定义键盘

#### ● [func advanceToNextInputMode()]()

切换到用户已启用的键盘列表中的下一个键盘。

#### ● [func dismissKeyboard()]()

从屏幕上消除自定义键盘。

#### ● [func handleInputModeList(from: UIView, with: UIEvent)]()

支持与用户已启用的键盘列表进行交互。

### 三、与文本输入对象进行交互

#### ● [var textDocumentProxy: UITextDocumentProxy]()

自定义键盘与文本输入对象进行交互的代理。

### 四、获得补充词汇

#### ● [func requestSupplementaryLexicon(completion: (UILexicon) -> Void)]()

Obtains a supplementary lexicon of term pairs for use in a custom keyboard.

### 五、更改自定义键盘的主要语言

#### ● [var primaryLanguage: String?]()

自定义键盘的主要语言。

### 六、配置键盘行为

#### ● [var needsInputModeSwitchKey: Bool]()

一个布尔值，指示键盘是否必须显示输入切换键。

#### ● [var hasFullAccess: Bool]()

一个布尔值，指示键盘是否具有完全访问权限。

### 七、实例属性

#### ● [var hasDictationKey: Bool]()

---

## 关系

### 继承自

[UIViewController]()

### 遵守

[CVarArg]()
[Equatable]()
[Hashable]()
[NSExtensionRequestHandling]()
[UIPasteConfigurationSupporting]()
[UIStateRestoring]()
[UITextInputDelegate]()
[UIUserActivityRestoring]()

---
## 其他内容