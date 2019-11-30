# evaluateAccessControl(_:operation:localizedReason:reply:)

鉴定给定操作的访问控制。

---

## 声明

```swift
func evaluateAccessControl(_ accessControl: SecAccessControl, 
                                 operation: LAAccessControlOperation, 
                           localizedReason: String, 
                                     reply: @escaping (Bool, Error?) -> Void)
```

## 参数

* **accessControl**

  要鉴定的访问控制。

* **operation**

  要鉴定的访问控制的操作。有关可能的值，请参阅[LAAccessControlOperation]()。

* **localizedReason**

  应用程序提供的请求验证的原因，它显示在呈现给用户的验证对话框中。

* **reply**

  访问控制鉴定完成时执行的闭包。这个闭包是在未指定线程上下文中的框架内部的专用队列上被调用的。

  * **success**

    如果策略鉴定成功则返回`true`，否则返回`false`。

  * **error**
    
    果策略鉴定成功返回`nil`，否则将提供一个错误对象。有关可能的错误码，请参阅[LAError.Code](./LAError-Code.md)。

## 说明

此方法异步鉴定访问控制。鉴定访问控制可涉及提示用户进行各种交互或认证。实际行为取决于访问控制和设备类型。它也可能受安装的配置文件影响。

你向用户展示的本地化字符串应该是一个明确的理由，说明你为什么要求用户自己进行身份验证，以及你将基于该身份验证采取什么操作。该字符串应该是用户当前的语言，并且应该简短明了。它不应该包含应用程序名称，因为应用程序名称会出现在验证对话框的其他地方。在macOS中，应用程序名称会出现在对话标题中；在iOS中，应用程序名称会出现在对话副标题中。

你不应该认为以前对访问控制的成功鉴定必然会导致之后鉴定会成功。访问控制鉴定可能由于各种原因而失败，包括被用户或被系统取消。

---
## 其他内容

### 鉴定访问控制

#### ● [var interactionNotAllowed: Bool](./interactionNotAllowed.md)

一个布尔值，指示身份验证是否可以交互。