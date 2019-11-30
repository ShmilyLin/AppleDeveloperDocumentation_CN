# localizedReason

向用户展示的认证对话框中显示的本地化释义。

---
## 声明

```swift
var localizedReason: String { get set }
```

## 说明

如果在[evaluatePolicy(_:localizedReason:reply:)](./evaluatePolicy-localizedReason-reply.md)中提供了认证原因，则此属性将被覆盖。

你向用户展示的本地化字符串应该是一个明确的理由，说明你为什么要求用户自己进行身份验证，以及你将基于该身份验证采取什么操作。该字符串应该是用户当前的语言，并且应该简短明了。它不应该包含应用程序名称，因为应用程序名称会出现在验证对话框的其他地方。在macOS中，应用程序名称会出现在对话标题中；在iOS中，应用程序名称会出现在对话副标题中。

--- 

## 其他内容

### 自定义身份验证提示

#### ● [var localizedFallbackTitle: String?](./localizedFallbackTitle.md)

在认证期间向用户呈现的对话中的返回按钮的本地化标题。

#### ● [var localizedCancelTitle: String?](./localizedCancelTitle.md)

在认证期间向用户呈现的对话中的取消按钮的本地化标题。