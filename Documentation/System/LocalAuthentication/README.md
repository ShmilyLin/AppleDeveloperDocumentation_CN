# LocalAuthentication

通过密码或生物识别技术向用户请求认证。

## 概述

Local Authentication框架提供了向用户请求指定安全策略认证的方法。

例如，要请求用户仅使用Face ID或Touch ID进行认证，您可以使用如下代码：

```swift
let myContext = LAContext()
let myLocalizedReasonString = <#String explaining why app needs authentication#>
 
var authError: NSError?
if #available(iOS 8.0, macOS 10.12.1, *) {
    if myContext.canEvaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, error: &authError) {
        myContext.evaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, localizedReason: myLocalizedReasonString) { success, evaluateError in
            if success {
                // 用户认证成功，可以采取适当的行动
            } else {
                // 用户认证失败，查看错误信息并采取适当的行动
            }
        }
    } else {
        // 无法调用策略，查看authError并向用户提供适当的消息
    }
} else {
    // 使用早期版本代码
}
```

## 专题

### 一、类

#### [class LAContext](./LAContext/)

LAContext对象表示一个认证上下文。LAContext类提供了一个编程接口，用于鉴定认证策略和访问控制，以及管理证书和注销认证上下文。

### 二、结构体

#### [struct LAError](./LAError.md)

### 三、参考

* [LocalAuthentication枚举]()
* [LocalAuthentication常量]()