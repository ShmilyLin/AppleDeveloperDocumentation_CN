# touchIDAuthenticationAllowableReuseDuration

Touch ID身份验证允许的重用时间间隔。

---
## 声明

```swift
var touchIDAuthenticationAllowableReuseDuration: TimeInterval { get set }
```

## 说明

如果设备在指定的时间间隔内使用Touch ID成功验证，则接收器的验证会自动成功，而不会提示用户输入Touch ID。

默认值为0，这意味着Touch ID身份验证无法重用。

Touch ID身份验证重用的最长允许持续时间由[LATouchIDAuthenticationMaximumAllowableReuseDuration]()常量指定。 如果将此属性设置为大于这个常量的值，则会使用这个常量提供的时间长度，无法指定更长的持续时间。

---
## 其他内容

### 管理证书

#### ● [func setCredential(Data?, type: LACredentialType)](./setCredential-type.md)

设置应用程序提供的证书，以在鉴定身份验证时使用。

#### ● [func isCredentialSet(LACredentialType)](./isCredentialSet.md)

返回是否设置了指定类型的证书。