# URLSessionTaskDelegate

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

`NSURLSessionTaskDelegate`协议定义了在使用任何类型的[URLSession]()任务时应该实现的特定任务的委托方法。 

---
## 概述

如果你正在使用下载任务，还需要实现[URLSessionDownloadDelegate]()协议中的方法。

如果你正在使用数据或上传任务，还需要实现[URLSessionDataDelegate]()协议中的方法。

> **Note**
> 
> 一个`NSURLSession`对象不需要`delegate`。如果未分配`delegate`，则使用系统提供的`delegate`，并且你必须提供完成回调以获取数据。

---
## 主题

### 一、协议方法

#### ● [func urlSession(URLSession, task: URLSessionTask, didReceive: URLAuthenticationChallenge, completionHandler: (URLSession.AuthChallengeDisposition, URLCredential?) -> Void)](./urlSession-task-didReceive-completionHandler.md)

响应来自远程服务器的认证请求，从`delegate`请求凭证。
Requests credentials from the delegate in response to an authentication request from the remote server.

#### ● [func urlSession(URLSession, task: URLSessionTask, didSendBodyData: Int64, totalBytesSent: Int64, totalBytesExpectedToSend: Int64)]()

定期通知`delegate`向服务器发送主体内容的进度。

#### ● [func urlSession(URLSession, task: URLSessionTask, needNewBodyStream: (InputStream?) -> Void)]()

当任务需要新的请求内容流发送到远程服务器时，告诉`delegate`。

#### ● [func urlSession(URLSession, task: URLSessionTask, willPerformHTTPRedirection: HTTPURLResponse, newRequest: URLRequest, completionHandler: (URLRequest?) -> Void)]()

告诉`delegate`远程服务器请求HTTP重定向。

#### ● [func urlSession(URLSession, task: URLSessionTask, didFinishCollecting: URLSessionTaskMetrics)]()

告诉`delegate`该会话完成了该任务的收集指标。

#### ● [class URLSessionTaskMetrics]()

一个`NSURLSessionTaskMetrics`对象封装了会话任务的度量标准。每个对象都包含[taskInterval]()和[redirectCount]()以及执行任务期间所做的每个请求/响应事务的指标。

#### ● [func urlSession(URLSession, task: URLSessionTask, didCompleteWithError: Error?)]()

告诉`delegate`任务完成了传输数据。

#### ● [func urlSession(URLSession, task: URLSessionTask, willBeginDelayedRequest: URLRequest, completionHandler: (URLSession.DelayedRequestDisposition, URLRequest?) -> Void)]()

告诉`delegate`，一个延迟的URL会话任务现在将开始加载。

#### ● [func urlSession(URLSession, taskIsWaitingForConnectivity: URLSessionTask)]()

告诉`delegate`，任务一直等待到合适的连接可用为止才会开始网络加载。

---

## 关系

### 继承自

[URLSessionDelegate](../URLSessionDelegate/)

### 被继承

* [AVAssetDownloadDelegate]()
* [URLSessionDataDelegate](../URLSessionDataDelegate/)
* [URLSessionDownloadDelegate]()
* [URLSessionStreamDelegate]()

---
## 其他内容