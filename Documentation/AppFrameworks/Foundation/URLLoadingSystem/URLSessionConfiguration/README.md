# URLSessionConfiguration

一个配置对象，用于定义URL会话的行为和策略。

---

## 概述

An URLSessionConfiguration object defines the behavior and policies to use when uploading and downloading data using an URLSession object. When uploading or downloading data, creating a configuration object is always the first step you must take. You use this object to configure the timeout values, caching policies, connection requirements, and other types of information that you intend to use with your URLSession object.

It is important to configure your URLSessionConfiguration object appropriately before using it to initialize a session object. Session objects make a copy of the configuration settings you provide and use those settings to configure the session. Once configured, the session object ignores any changes you make to the URLSessionConfiguration object. If you need to modify your transfer policies, you must update the session configuration object and use it to create a new URLSession object.

> Note
>
> In some cases, the policies defined in this configuration may be overridden by policies specified by an NSURLRequest object provided for a task. Any policy specified on the request object is respected unless the session’s policy is more restrictive. For example, if the session configuration specifies that cellular networking should not be allowed, the NSURLRequest object cannot request cellular networking.

For more information about using configuration objects to create sessions, see URLSession.

## 主题

### 一、创建一个会话配置对象

#### ● [class var `default`: URLSessionConfiguration]()
Returns a newly created default session configuration object.

#### ● [class var ephemeral: URLSessionConfiguration]()
Returns a session configuration that uses no persistent storage for caches, cookies, or credentials.

#### ● [class func background(withIdentifier: String)]()
Returns a session configuration object that allows HTTP and HTTPS uploads or downloads to be performed in the background.

### 二、设置常规属性

#### ● [var identifier: String?]()
The background session identifier of the configuration object.

#### ● [var httpAdditionalHeaders: [AnyHashable : Any]?]()
A dictionary of additional headers to send with requests.

#### ● [var networkServiceType: NSURLRequest.NetworkServiceType]()
The type of network service.

#### ● [var allowsCellularAccess: Bool]()
A Boolean value that determines whether connections should be made over a cellular network.

#### ● [var timeoutIntervalForRequest: TimeInterval]()
The timeout interval to use when waiting for additional data.

#### ● [var timeoutIntervalForResource: TimeInterval]()
The maximum amount of time that a resource request should be allowed to take.

#### ● [var sharedContainerIdentifier: String?]()
The identifier for the shared container into which files in background URL sessions should be downloaded.

#### ● [var waitsForConnectivity: Bool]()
A Boolean value that indicates whether the session should wait for connectivity to become available, or fail immediately.

### 三、设置Cookie策略

#### ● [var httpCookieAcceptPolicy: HTTPCookie.AcceptPolicy]()
A policy constant that determines when cookies should be accepted.

#### ● [var httpShouldSetCookies: Bool]()
A Boolean value that determines whether requests should contain cookies from the cookie store.

#### ● [var httpCookieStorage: HTTPCookieStorage?]()
The cookie store for storing cookies within this session.

#### ● [class HTTPCookieStorage]()
A singleton object (shared instance) that manages storage of cookies.

#### ● [class HTTPCookie]()
An object that represents an HTTP cookie. It is an immutable object, initialized from a dictionary containing the cookie attributes.

### 四、设置安全策略

#### ● [var tlsMaximumSupportedProtocol: SSLProtocol]()
The maximum TLS protocol version that the client should request when making connections in this session.

#### ● [var tlsMinimumSupportedProtocol: SSLProtocol]()
The minimum TLS protocol that should be accepted during protocol negotiation.

#### ● [var urlCredentialStorage: URLCredentialStorage?]()
A credential store that provides credentials for authentication.

### 五、设置缓存策略

#### ● [var urlCache: URLCache?]()
The URL cache for providing cached responses to requests within the session.

#### ● [var requestCachePolicy: NSURLRequest.CachePolicy]()
A predefined constant that determines when to return a response from the cache.

### 六、支持后台转移

#### ● [var sessionSendsLaunchEvents: Bool]()
A Boolean value that indicates whether the app should be resumed or launched in the background when transfers finish.

#### ● [var isDiscretionary: Bool]()
A Boolean value that determines whether background tasks can be scheduled at the discretion of the system for optimal performance.

#### ● [var shouldUseExtendedBackgroundIdleMode: Bool]()

### 七、支持自定义协议

#### ● [var protocolClasses: [AnyClass]?]()
An array of extra protocol subclasses that handle requests in a session.

#### ● [class URLProtocol](./URLProtocol/)

一个`NSURLProtocol`对象处理加载特定协议的URL数据。`NSURLProtocol`类本身是一个抽象类，它提供了用于处理具有特定URL scheme的URL的基础结构。你可以通过创建子类来让你的应用支持的任何自定义协议或URL scheme。

### 八、支持多路径TCP

#### ● [Improving Network Reliability Using Multipath TCP]()
Use the available radios in iOS devices to improve your app’s network reliability and performance.

#### ● [var multipathServiceType: URLSessionConfiguration.MultipathServiceType]()
A service type that specifies the Multipath TCP connection policy for transmitting data over Wi-Fi and cellular interfaces.

#### ● [enum URLSessionConfiguration.MultipathServiceType]()
Constants that specify the type of service that Multipath TCP uses.

### 九、设置HTTP策略和代理属性

#### ● [var httpMaximumConnectionsPerHost: Int]()
The maximum number of simultaneous connections to make to a given host.

#### ● [var httpShouldUsePipelining: Bool]()
A Boolean value that determines whether the session should use HTTP pipelining.

#### ● [var connectionProxyDictionary: [AnyHashable : Any]?]()
A dictionary containing information about the proxy to use within this session.

### 十、支持连接变化

#### ● [var waitsForConnectivity: Bool]()
A Boolean value that indicates whether the session should wait for connectivity to become available, or fail immediately.

### 十一、已弃用的方法

#### ● [~~class func backgroundSessionConfiguration(String)~~]()**【已弃用】**
Returns a session configuration object that allows HTTP and HTTPS uploads or downloads to be performed in the background.

Deprecated

---

## 关系

### 继承自

[NSObject]()

### 遵守

[CVarArg]()
[Equatable]()
[Hashable]()
[NSCopying]()

---
## 其他内容

