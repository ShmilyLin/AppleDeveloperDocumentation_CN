# deviceOwnerAuthentication

表示设备所有者可以使用生物识别或设备密码进行身份验证。

---
## 声明

```swift
case deviceOwnerAuthentication = 2
```

## 说明

如果Touch ID或Face ID可用，已注册且被未禁用，则首先要求用户验证Touch ID或Face ID。否则，用户会被要求输入设备密码。如果设备密码未启用，则策略鉴定失败。6次尝试失败后，密码验证功能被禁用，它们之间的延迟逐渐增加。

身份验证对话框包含一个具有默认标题的取消按钮，可以使用[localizedCancelTitle]()属性像返回按钮一样进行定制，后者可以使用[localizedFallbackTitle]()属性进行定制。点击返回按钮切换认证方法，以询问用户设备密码。点击取消按钮导致[evaluatePolicy(_:localizedReason:reply:) 方法的回调返回失败。
