# urlSession(_:task:didReceive:completionHandler:)

<div style="border:1px solid lightgray;border-radius: 5px;margin-bottom:20px;">
    <div style="padding-left:20px;padding-top:10px;padding-bottom:10px">
        <strong>SDKs</strong>
        <div style="overflow:hidden">
            <div style="float:left;color:#666666;">
                iOS 7.0+
            </div>
        </div>
        <div style="overflow:hidden">
            <div style="float:left;color:#666666;">
                macOS 10.9+
            </div>
        </div>
        <div style="overflow:hidden">
            <div style="float:left;color:#666666;">
                tvOS 9.0+
            </div>
        </div>
        <div style="overflow:hidden">
            <div style="float:left;color:#666666;">
                watchOS 2.0+
            </div>
        </div>
    </div>
    <div style="width: 100%;height:1px;background-color:lightgray;"></div>
    <div style="padding-left:20px;padding-top:10px;padding-bottom:10px">
        <strong>Framework</strong>
        <div style="color:#666666;">
            Foundation
        </div>
    </div>
</div>

响应来自远程服务器的认证请求，从`delegate`请求凭证。

---
## 声明

```swift
optional func urlSession(_ session: URLSession, 
                              task: URLSessionTask, 
              didReceive challenge: URLAuthenticationChallenge, 
                 completionHandler: @escaping (URLSession.AuthChallengeDisposition, URLCredential?) -> Void)
```

## 参数

* **session**

  包含需要身份验证的请求任务的会话。

* **task**

  需要验证的请求任务。

* **challenge**

  包含身份验证请求的对象。

* **completionHandler**

  你的`delegate`方法必须调用的处理。其参数是：
  
  * `disposition`——描述如何处理验证的几个常量之一。
  * `credential`——如果`disposition`是`NSURLSessionAuthChallengeUseCredential`，则`credential`是用于认证的证书，否则是`NULL`。

## 说明

此方法处理任务级别的身份验证挑战。 URLSessionDelegate协议还提供会话级别的身份验证委托方法。 所调用的方法取决于身份验证挑战的类型：

This method handles task-level authentication challenges. The URLSessionDelegate protocol also provides a session-level authentication delegate method. The method called depends on the type of authentication challenge: