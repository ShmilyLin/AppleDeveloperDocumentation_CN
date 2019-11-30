# URLSessionDelegate

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

`NSURLSessionDelegate`协议描述[URLSession]()对象在其`delegates`上调用以处理会话级别事件的方法。

---
## 概述

除了此协议中定义的方法之外，大多数`delegates`还应实现[URLSessionTaskDelegate](./URLSessionTaskDelegate/)，[URLSessionDataDelegate](./URLSessionDataDelegate/)和[URLSessionDownloadDelegate]()协议中的部分或全部方法来处理任务级别的事件。

> **注意**
> 
> 一个`NSURLSession`对象不需要`delegate`。如果未分配`delegate`，则使用系统提供的`delegate`，并且你必须提供完成回调以获取数据。

---
## 主题

### 一、代理方法

#### ● [func urlSession(URLSession, didBecomeInvalidWithError: Error?)]()

通知URL会话该会话已失效。

#### ● [func urlSession(URLSession, didReceive: URLAuthenticationChallenge, completionHandler: (URLSession.AuthChallengeDisposition, URLCredential?) -> Void)]()

响应来自远程服务器的会话级别认证请求，从`delegate`请求证书。

#### ● [func urlSessionDidFinishEvents(forBackgroundURLSession: URLSession)]()

告诉`delegate`，会话中所有的消息都已发送。

### 二、常量

#### ● [enum URLSession.AuthChallengeDisposition]()

响应于认证质询，由会话或任务`delegates`传递的常量代表所提供的继续闭包。
Constants passed by session or task delegates to the provided continuation block in response to an authentication challenge.

---
## 关系

### 继承自

[NSObjectProtocol]()

### 被继承

* [URLSessionTaskDelegate](../URLSessionTaskDelegate/)

---
## 其他内容