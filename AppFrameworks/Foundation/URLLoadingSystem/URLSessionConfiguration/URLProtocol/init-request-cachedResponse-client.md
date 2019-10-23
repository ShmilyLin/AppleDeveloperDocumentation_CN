# init(request:cachedResponse:client:)

初始化并返回一个协议对象。

---

## 声明

```swift
    init(request: URLRequest, 
  cachedResponse: CachedURLResponse?, 
          client: URLProtocolClient?)
```

## 参数

* **request**

  URL协议对象的URL请求。这个请求会被保留。

* **cachedResponse**

  请求的缓存响应; 如果请求没有现有的缓存响应，则可以为`nil`。

* **client**

  `client`是用来与URL加载系统进行通信的实现了[URLProtocolClient](./URLProtocolClient/)协议的对象。 该`client`对象会被保留。

## 说明

子类应该重写此方法来执行任何自定义初始化。应用程序不应该显式调用此方法。

这是`NSURLProtocol`指定的初始化。

---
## 其他内容

### 创建协议对象

#### ● [init(task: URLSessionTask, cachedResponse: CachedURLResponse?, client: URLProtocolClient?)](./init-task-cachedResponse-client.md)

### 相关文档

#### ● [URL会话编程指南](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/URLLoadingSystem/URLLoadingSystem.html#//apple_ref/doc/uid/10000165i)