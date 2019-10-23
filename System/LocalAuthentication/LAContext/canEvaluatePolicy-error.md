# canEvaluatePolicy(_:error:)

检查身份验证策略鉴定是否可以使用。

---

## 声明

```swift
func canEvaluatePolicy(_ policy: LAPolicy, 
                          error: NSErrorPointer) -> Bool
```

## 参数

* **policy**

  要鉴定的策略。有关可能的值，请参阅[LAPolicy]()。

* **error**

  如果发生错误，返回一个包含错误信息的NSError对象。有关可能的错误代码，请参阅[LAError.Code](./LAError-Code.md)。

  如果你不需要错误信息，你可以将此参数设置为nil。

## 返回值

如果这个策略可以被鉴定则返回`true`，否则返回`false`。

## 说明

策略可能有必须达成的条件，才能有机会成功的进行身份验证。 例如，使用生物识别技术的策略需要Touch ID或Face ID未被禁用。

此方法的返回值可能随时间而改变，所以你不应该将此值存储以供将来在你的应用程序中使用。在你的应用进入后台之前，该值将保持不变。

### 特殊情况

此方法不能在[evaluatePolicy(_:localizedReason:reply:)](./evaluatePolicy-localizedReason-reply.md)的闭包中使用，否则会导致锁死。

---
## 其他内容

### 鉴定身份验证策略

#### ● [func evaluatePolicy(LAPolicy, localizedReason: String, reply: (Bool, Error?) -> Void)](./evaluatePolicy-localizedReason-reply.md)

鉴定指定的策略域。

#### ● [var evaluatedPolicyDomainState: Data?](./evaluatedPolicyDomainState.md)

鉴定的策略域的当前状态。

#### ● [var biometryType: LABiometryType](./biometryType.md)

设备支持的生物认证类型。

#### ● [~~var maxBiometryFailures: NSNumber?~~](./maxBiometryFailures.md)**【已废弃】**

设置生物特征验证期间允许失败的次数限制。