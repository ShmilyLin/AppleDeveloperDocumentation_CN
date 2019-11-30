# URLProtocol

一个`NSURLProtocol`对象处理加载特定协议的URL数据。`NSURLProtocol`类本身是一个抽象类，它提供了用于处理具有特定URL scheme的URL的基础结构。你可以通过创建子类来让你的应用支持的任何自定义协议或URL scheme。

---
## 概述

应用程序永远不需要直接实例化`NSURLProtocol`子类。当一个下载开始时，系统创建相应的协议对象来处理相应的URL请求。你所要做的就是定义你的协议类，并在应用程序启动时调用[registerClass(_: )](./registerClass.md)类方法，以便让系统知道你的协议。

> **注意**
>
> 你不能在watchOS 2以及更高版本中使用此类定义自定义URL schemes和协议。

为了支持特定协议请求的自定义，鼓励你使用任何你需要的自定义API在`NSURLRequest`和`NSMutableURLRequest`上定义类。需要以这种方式扩展`NSURLRequest`和`NSMutableURLRequest`的功能的协议实现者可以使用`NSURLProtocol`的类方法[property(forKey:in:)](./property-forKey-in.md)和[setProperty(_:forKey:in:)](./setProperty-forKey-in.md)来存储和检索特定协议的请求数据。

协议实现者的基本职责是为每个成功处理的请求创建一个`NSURLResponse`。协议实现者可能希望创建一个自定义的、可变的`NSURLResponse`类来提供特定协议的信息。

---
## 主题

### 一、创建协议对象

#### ● [init(request: URLRequest, cachedResponse: CachedURLResponse?, client: URLProtocolClient?)](./init-request-cachedResponse-client.md)

初始化并返回一个协议对象。

#### ● [init(task: URLSessionTask, cachedResponse: CachedURLResponse?, client: URLProtocolClient?)](./init-task-cachedResponse-client.md)

### 二、注册和取消注册协议类

#### ● [class func registerClass(AnyClass)](./registerClass.md)

尝试注册`NSURLProtocol`的子类，使其对URL加载系统可见。

#### ● [class func unregisterClass(AnyClass)](./unregisterClass.md)

取消注册指定的`NSURLProtocol`的子类。

### 三、确定子类是否可以处理请求

#### ● [class func canInit(with: URLRequest)](./canInit-with.md)

返回协议子类是否可以处理指定的请求。

#### ● [class func canInit(with: URLSessionTask)](./canInit-with-1.md)

返回协议子类是否可以处理指定的任务。

### 四、获取和设置请求属性

#### ● [class func property(forKey: String, in: URLRequest)](./property-forKey-in.md)

返回与指定请求中与指定key关联的属性。

#### ● [class func setProperty(Any, forKey: String, in: NSMutableURLRequest)](./setProperty-forKey-in.md)

设置与指定请求中与指定key关联的属性。

#### ● [class func removeProperty(forKey: String, in: NSMutableURLRequest)](./removeProperty-forKey-in.md)

移除与指定请求中与指定key关联的属性。

### 五、提供一个规范版本的请求

#### ● [class func canonicalRequest(for: URLRequest)](./canonicalRequest-for.md)

返回一个指定请求的规范版本。

### 六、确定请求是否是缓存等效的

#### ● [class func requestIsCacheEquivalent(URLRequest, to: URLRequest)](./requestIsCacheEquivalent-to.md)

返回两个请求是否有相同的`cache purposes`。

### 七、开始和停止下载

#### ● [func startLoading()](./startLoading.md)

开始特定协议的请求加载。

#### ● [func stopLoading()](./stopLoading.md)

停止特定协议的请求加载。

### 八、获取协议属性

#### ● [var cachedResponse: CachedURLResponse?](./cachedResponse.md)

协议的缓存响应。

#### ● [var client: URLProtocolClient?](./client.md)

协议用来与URL加载系统进行通信的对象。

#### ● [var request: URLRequest](./request.md)

协议的请求。

#### ● [var task: URLSessionTask?](./task.md)

协议的任务。

### 九、支持类型

#### ● [protocol URLProtocolClient](./URLProtocolClient/)

`NSURLProtocolClient`协议提供`NSURLProtocol`子类用于与URL加载系统进行通信的接口。应用程序永远不需要实现这个协议。

---
## 关系

### 继承自

* [NSObject]()

### 遵守

* [CVarArg]() 
* [Equatable]()
* [Hashable]()

---

## 其他内容

