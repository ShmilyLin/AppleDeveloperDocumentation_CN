# localizedCancelTitle

在认证期间向用户呈现的对话中的取消按钮的本地化标题。

---

## 声明

```swift
var localizedCancelTitle: String? { get set }
```

## 说明

该字符串应该以用户当前的语言提供，并且应该简短明了。

---
## 其他内容

### 自定义身份验证提示

#### ● [var localizedReason: String](./localizedReason.md)

向用户展示的认证对话框中显示的本地化释义。

#### ● [var localizedFallbackTitle: String?](./localizedFallbackTitle.md)

在认证期间向用户呈现的对话中的返回按钮的本地化标题。

### 相关文档

#### ● [case deviceOwnerAuthenticationWithBiometrics](./LAPolicy/deviceOwnerAuthenticationWithBiometrics.md)

表示设备所有者必须使用生物识别进行身份验证。

#### ● [case deviceOwnerAuthentication](./LAPolicy/deviceOwnerAuthentication.md)

表示设备所有者可以使用生物识别或设备密码进行身份验证。