# deviceOwnerAuthenticationWithBiometrics

表示设备所有者必须使用生物识别进行身份验证。

---

## 声明

```swift
case deviceOwnerAuthenticationWithBiometrics = 1
```

## 说明

如果Touch ID或Face ID不可用或未注册，则策略鉴定失败。在连续三次认证Touch ID或Face ID不成功后，策略鉴定将失败。在五次认证失败之后，Touch ID和Face ID身份验证都被禁用，要求用户输入设备密码才能重新使用。

身份验证对话框包含一个取消按钮和一个返回按钮。返回按钮允许用户使用设备密码进行验证。按钮标题可以使用[localizedCancelTitle](../localizedCancelTitle.md)属性或[localizedFallbackTitle](../localizedFallbackTitle.md)属性进行自定义。

返回按钮最初是隐藏的。对于Face ID，在第一次认证失败之后，将提示用户再次尝试Face ID认证或取消认证。在第二次Face ID认证失败之后，将显示返回按钮。对于Touch ID，在第一次Touch ID认证失败后显示返回按钮。

点击取消按钮或返回按钮会导致[evaluatePolicy(_:localizedReason:reply:)](../evaluatePolicy-localizedReason-reply.md)方法回调失败结果。

