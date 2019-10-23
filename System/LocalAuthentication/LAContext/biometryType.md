# biometryType

设备支持的生物认证类型。

---
## 声明

```swift
var biometryType: LABiometryType { get }
```

## 说明

使用此属性的值可确保你创建的任何身份验证相关的用户提示信息与设备的生物识别功能相匹配。例如，如果此属性的值是[faceID]()，请不要在身份验证提示中出现Touch ID。

该属性仅在一个生物特征识别策略的[canEvaluatePolicy(_:error:)](./canEvaluatePolicy-error.md)成功执行时设置。默认值是[LABiometryNone]()。

---
## 其他内容

### 鉴定身份验证策略

#### ● [func canEvaluatePolicy(LAPolicy, error: NSErrorPointer)](./canEvaluatePolicy-error.md)

检查身份验证策略鉴定是否可以使用。

#### ● [func evaluatePolicy(LAPolicy, localizedReason: String, reply: (Bool, Error?) -> Void)](./evaluatePolicy-localizedReason-reply.md)

鉴定指定的策略域。

#### ● [var evaluatedPolicyDomainState: Data?](./evaluatedPolicyDomainState.md)

鉴定的策略域的当前状态。

#### ● [~~var maxBiometryFailures: NSNumber?~~](./maxBiometryFailures.md)**【已废弃】**

设置生物特征验证期间允许失败的次数限制。