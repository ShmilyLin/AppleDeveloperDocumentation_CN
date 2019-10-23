# LAContext

`LAContext`对象表示一个认证上下文。`LAContext`类提供了一个编程接口，用于鉴定认证策略和访问控制，以及管理证书和注销认证上下文。

---
## 概述

身份验证上下文用于鉴定身份验证策略，允许应用程序请求用户使用生物识别方法进行身份验证。

> **重要**
>
> 如果您的应用允许使用生物识别身份验证，则需要在应用的`Info.plist`文件中包含[NSFaceIDUsageDescription]() key。 如果该key不存在，授权请求可能会直接失败。

---
## 专题

### 一、鉴定身份验证策略

#### ● [func canEvaluatePolicy(LAPolicy, error: NSErrorPointer)](./canEvaluatePolicy-error.md)

检查身份验证策略鉴定是否可以使用。

#### ● [func evaluatePolicy(LAPolicy, localizedReason: String, reply: (Bool, Error?) -> Void)](./evaluatePolicy-localizedReason-reply.md)

鉴定指定的策略域。

#### ● [var evaluatedPolicyDomainState: Data?](./evaluatedPolicyDomainState.md)

鉴定的策略域的当前状态。

#### ● [var biometryType: LABiometryType](./biometryType.md)

设备支持的生物认证类型。

#### ● [~~var maxBiometryFailures: NSNumber?~~](./maxBiometryFailures.md)**【已废弃】**

设置生物特征验证期间允许失败的次数限制。

### 二、鉴定访问控制

#### ● [func evaluateAccessControl(SecAccessControl, operation: LAAccessControlOperation, localizedReason: String, reply: (Bool, Error?) -> Void)](./evaluateAccessControl-operation-localizedReason-reply.md)

鉴定给定操作的访问控制。

#### ● [var interactionNotAllowed: Bool](./interactionNotAllowed.md)

一个布尔值，指示身份验证是否可以交互。

### 三、自定义身份验证提示

#### ● [var localizedReason: String](./localizedReason.md)

向用户展示的认证对话框中显示的本地化释义。

#### ● [var localizedFallbackTitle: String?](./localizedFallbackTitle.md)

在认证期间向用户呈现的对话中的返回按钮的本地化标题。

#### ● [var localizedCancelTitle: String?](./localizedCancelTitle.md)

在认证期间向用户呈现的对话中的取消按钮的本地化标题。

### 四、管理证书

#### ● [func setCredential(Data?, type: LACredentialType)](./setCredential-type.md)

设置应用程序提供的证书，以在鉴定身份验证时使用。

#### ● [func isCredentialSet(LACredentialType)](./isCredentialSet.md)

返回是否设置了指定类型的证书。

#### ● [var touchIDAuthenticationAllowableReuseDuration: TimeInterval](./touchIDAuthenticationAllowableReuseDuration.md)

Touch ID身份验证允许的重用时间间隔。

### 五、销毁验证上下文

#### ● [func invalidate()](./invalidate.md)

销毁验证上下文。

### 六、常量

#### ● [本地认证错误域]()

Local Authentication框架的错误域。

#### ● [enum LAError.Code](./LAErrorCode/)

鉴定策略时可能返回的错误码。

#### ● [enum LAPolicy](./LAPolicy/)

指定可接受哪种形式的认证策略。

#### ● [enum LACredentialType](./LACredentialType/)

要用于身份验证的证书类型。

#### ● [enum LAAccessControlOperation](./LAAccessControlOperation/)

通过[evaluateAccessControl(_:operation:localizedReason:reply:)](./evaluateAccessControl-operation-localizedReason-reply.md)方法要鉴定访问控制的操作。

#### ● [Touch ID Authentication Reuse]()

在[touchIDAuthenticationAllowableReuseDuration](./touchIDAuthenticationAllowableReuseDuration.md)属性中使用的Touch ID身份验证重用间隔时间。

---
## 其他内容

### 继承自

[NSObject]()

### 遵守的协议

* [CVarArg]()
* [Equatable]()
* [Hashable]()