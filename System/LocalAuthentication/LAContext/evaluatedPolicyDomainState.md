# evaluatedPolicyDomainState

鉴定的策略域的当前状态。

---
## 声明

```swift
var evaluatedPolicyDomainState: Data? { get }
```

## 说明

仅当一个生物特征策略的[canEvaluatePolicy(_:error:)](./canEvaluatePolicy-error.md)方法成功执行或[evaluatePolicy(_:localizedReason:reply:)](./evaluatePolicy-localizedReason-reply.md)方法被调用且成功执行生物特征身份验证时，此属性才会返回值。否则，返回`nil`。

返回的数据是不透明的结构。它可用于与此属性返回的其他值进行比较，以确定授权数据库是否已更新。但是，这些数据无法确定变更的性质。

---
## 其他内容

### 鉴定身份验证策略

#### ● [func canEvaluatePolicy(LAPolicy, error: NSErrorPointer)](./canEvaluatePolicy-error.md)

检查身份验证策略鉴定是否可以使用。

#### ● [func evaluatePolicy(LAPolicy, localizedReason: String, reply: (Bool, Error?) -> Void)](./evaluatePolicy-localizedReason-reply.md)

鉴定指定的策略域。

#### ● [var biometryType: LABiometryType](./biometryType.md)

设备支持的生物认证类型。

#### ● [~~var maxBiometryFailures: NSNumber?~~](./maxBiometryFailures.md)**【已废弃】**

设置生物特征验证期间允许失败的次数限制。