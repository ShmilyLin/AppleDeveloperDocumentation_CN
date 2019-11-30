# ~~maxBiometryFailures~~

【已在iOS 10.0中废弃】

设置生物特征验证期间允许失败的次数限制。

---
## 声明

```swift
var maxBiometryFailures: NSNumber? { get set }
```

---
## 其他内容

### 鉴定身份验证策略

#### ● [func canEvaluatePolicy(LAPolicy, error: NSErrorPointer)](./canEvaluatePolicy-error.md)

检查身份验证策略鉴定是否可以使用。

#### ● [func evaluatePolicy(LAPolicy, localizedReason: String, reply: (Bool, Error?) -> Void)](./evaluatePolicy-localizedReason-reply.md)

鉴定指定的策略域。

#### ● [var evaluatedPolicyDomainState: Data?](./evaluatedPolicyDomainState.md)

鉴定的策略域的当前状态。

#### ● [var biometryType: LABiometryType](./biometryType.md)

设备支持的生物认证类型。