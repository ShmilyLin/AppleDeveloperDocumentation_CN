# evaluatePolicy(_:localizedReason:reply:)

鉴定指定的策略域。

---

## 声明

```swift
func evaluatePolicy(_ policy: LAPolicy, 
             localizedReason: String, 
                       reply: @escaping (Bool, Error?) -> Void)
```

## 参数

* **policy**

  要鉴定的策略。有关可能的值，请参阅[LAPolicy]()。

* **localizedReason**

  应用程序提供的请求验证的原因，它显示在呈现给用户的验证对话框中。

* **reply**

  在策略鉴定结束时执行的闭包。这个闭包是在未指定线程上下文中的框架内部的专用队列上被调用的。你不可以在这个闭包中调用[canEvaluatePolicy(_:error:)](./canEvaluatePolicy-error.md)，否则可能会导致锁死。

  * **success**

    如果策略鉴定成功则返回`true`，否则返回`false`。

  * **error**
    
    果策略鉴定成功返回`nil`，否则将提供一个错误对象。有关可能的错误码，请参阅[LAError.Code](./LAError-Code.md)。

## 说明

此方法异步鉴定认证策略。鉴定策略可能涉及提示用户进行各种交互或认证。实际行为取决于鉴定的策略和设备类型。该行为还可能受安装的配置文件影响。

在验证对话框中向用户显示的本地化字符串中，需要提供请求验证的明确原因，并描述操作结果。提供的信息要简明明了，并以用户的本机的语言显示。请勿包含已在验证对话框中显示的应用程序名称（在macOS中，应用名称会自动显示在对话框标题中；在iOS中，应用名称会自动显示在副标题中）。

不要以为以前成功的策略鉴定意味着未来的鉴定也会成功。策略鉴定可能由于各种原因而失败，包括被用户或被系统取消鉴定。

---
## 其他内容

### 鉴定身份验证策略

#### ● [func canEvaluatePolicy(LAPolicy, error: NSErrorPointer)](./canEvaluatePolicy-error.md)

检查身份验证策略鉴定是否可以使用。

#### ● [var evaluatedPolicyDomainState: Data?](./evaluatedPolicyDomainState.md)

鉴定的策略域的当前状态。

#### ● [var biometryType: LABiometryType](./biometryType.md)

设备支持的生物认证类型。

#### ● [~~var maxBiometryFailures: NSNumber?~~](./maxBiometryFailures.md)**【已废弃】**

设置生物特征验证期间允许失败的次数限制。