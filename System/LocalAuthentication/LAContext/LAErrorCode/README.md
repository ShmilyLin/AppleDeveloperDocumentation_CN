# LAError.Code

鉴定策略时可能返回的错误码。

---

## 主题

### 一、常量

#### ● [case authenticationFailed](./authenticationFailed.md)

身份验证失败，因为用户未能提供有效的凭据。

#### ● [case appCancel](./appCancel.md)

#### ● [case invalidContext](./invalidContext.md)

#### ● [case notInteractive](./notInteractive.md)

#### ● [case passcodeNotSet](./passcodeNotSet.md)

由于密码未在设备上设置，身份验证无法启动。

#### ● [case systemCancel](./systemCancel.md)

身份验证被系统取消——例如，如果另一个应用程序在身份验证对话框启动时进入前台。

#### ● [~~case touchIDLockout~~](./touchIDLockout.md)**【已废弃】**

#### ● [~~case touchIDNotAvailable~~](./touchIDNotAvailable.md)**【已废弃】**

由于Touch ID在设备上不可用，身份验证无法启动。

#### ● [~~case touchIDNotEnrolled~~](./touchIDNotEnrolled.md)**【已废弃】**

由于Touch ID没有注册手指，身份验证无法启动。

#### ● [case userCancel](./userCancel.md)

由于用户点击验证对话框中的取消按钮，身份验证被取消。

#### ● [case userFallback](./userFallback.md)

由于用户点击了认证对话框中的返回按钮，因此认证被取消，但认证策略不存在返回操作内容。

### 二、类属性

#### ● [static var biometryLockout: LAError.Code](./biometryLockout.md)

由于认证失败太多，用户已被锁定在生物认证之外，所以无法继续认证。

#### ● [static var biometryNotAvailable: LAError.Code](./biometryNotAvailable.md)

由于设备不支持生物认证，认证无法启动。

#### ● [static var biometryNotEnrolled: LAError.Code](./biometryNotEnrolled.md)

由于用户尚未注册生物特征身份验证，身份验证无法启动。