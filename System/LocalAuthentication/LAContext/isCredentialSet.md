# isCredentialSet(_: )

返回是否设置了指定类型的证书。

---
## 声明

```swift
func isCredentialSet(_ type: LACredentialType) -> Bool
```

## 参数

* **type**

  证书的类型。有关可能的值，请参阅[LACredentialType]()。

## 返回值

如果证书已经被设置则返回`true`，否则返回`false`。

---
## 其他内容

### 管理证书

#### ● [func setCredential(Data?, type: LACredentialType)](./setCredential-type.md)

设置应用程序提供的证书，以在鉴定身份验证时使用。

#### ● [var touchIDAuthenticationAllowableReuseDuration: TimeInterval](./touchIDAuthenticationAllowableReuseDuration.md)

Touch ID身份验证允许的重用时间间隔。