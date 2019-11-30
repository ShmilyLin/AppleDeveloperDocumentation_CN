# setCredential(_:type:)

设置应用程序提供的证书，以在鉴定身份验证时使用。

---
## 声明

```swift
func setCredential(_ credential: Data?, 
                           type: LACredentialType) -> Bool
```

## 参数

* **credential**

  鉴定认证上下文时使用的凭证。

  将此参数设置为`nil`将删除所有指定类型的现有证书。

* **type**

  指定的证书的类型。有关可能的值，请参阅[LACredentialType]()。

## 返回值

如果证书被设置则返回`true`，否则返回`false`。

---
## 其他内容

### 管理证书

#### ● [func isCredentialSet(LACredentialType)](./isCredentialSet.md)

返回是否设置了指定类型的证书。

#### ● [var touchIDAuthenticationAllowableReuseDuration: TimeInterval](./touchIDAuthenticationAllowableReuseDuration.md)

Touch ID身份验证允许的重用时间间隔。