# URLSessionDataDelegate

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

`NSURLSessionDataDelegate`协议定义了[URLSession]()对象的`delegate`可以实现的方法，以处理特定数据任务和上传任务的任务级事件。

---
## 概述

你的会话`delegate`还应实现[URLSessionTaskDelegate](../URLSessionTaskDelegate/)协议中的方法，以处理所有任务通用的任务级别事件以及[URLSessionDelegate](../URLSessionDelegate/)协议中用于处理会话级别事件的方法。

> **注意**
> 
> 一个`NSURLSession`对象不需要`delegate`。如果未分配`delegate`，则在该会话初始化时必须提供完成回调以获取数据。
> 
> 完成处理闭包主要用作自定义`delegate`的替代方法。如果使用带有完成处理闭包的方法创建任务，则不会调用响应和数据传递的协议方法。

---

## 主题

### 一、协议方法

#### ● [func urlSession(URLSession, dataTask: URLSessionDataTask, didReceive: URLResponse, completionHandler: (URLSession.ResponseDisposition) -> Void)]()

告诉`delegate`，数据任务从服务器收到初始回复（`headers`）。

#### ● [func urlSession(URLSession, dataTask: URLSessionDataTask, didBecome: URLSessionDownloadTask)]()

告诉`delegate`，数据任务已更改为下载任务。

#### ● [func urlSession(URLSession, dataTask: URLSessionDataTask, didBecome: URLSessionStreamTask)]()

告诉`delegate`，数据任务已更改为流任务。

#### ● [func urlSession(URLSession, dataTask: URLSessionDataTask, didReceive: Data)]()

告诉`delegate`，该数据任务已经收到了一些预期的数据。

#### ● [func urlSession(URLSession, dataTask: URLSessionDataTask, willCacheResponse: CachedURLResponse, completionHandler: (CachedURLResponse?) -> Void)]()

询问`delegate`，数据（或上传）任务是否应将响应存储在缓存中。

### 二、常量

#### ● [enum URLSession.ResponseDisposition]()

指示数据或上传会话在接收到初始`headers`后应如何继续进行的常量。

---
## 关系

### 继承自

[URLSessionTaskDelegate](../URLSessionTaskDelegate/)

---

## 其他内容