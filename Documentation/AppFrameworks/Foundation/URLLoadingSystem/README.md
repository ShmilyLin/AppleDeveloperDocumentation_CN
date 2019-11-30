# URL Loading System

与URL进行交互并使用标准Internet协议与服务器进行通信。

## 概述

The URL Loading System provides access to resources identified by URLs, using standard protocols like https or custom protocols you create. Loading is performed asynchronously, so your app can remain responsive and handle incoming data or errors as they arrive.

You use a URLSession instance to create one or more URLSessionTask instances, which can fetch and return data to your app, download files, or upload data and files to remote locations. To configure a session, you use a URLSessionConfiguration object, which controls behavior like how to use caches and cookies, or whether to allow connections on a cellular network.

You can use one session repeatedly to create tasks. For example, a web browser might have separate sessions for regular and private browsing use, where the private session doesn’t cache its data. Figure 1 shows how two sessions with these configurations can then create multiple tasks.

![Figure 1 Creating tasks from URL sessions](https://docs-assets.developer.apple.com/published/4bf9c6d271/6789dd96-afdc-4c18-b8eb-01f9012dc04d.png)

Each session is associated with a delegate to receive periodic updates (or errors). The default delegate calls a completion handler block that you provide; if you choose to provide your own custom delegate, this block is not called.

You can configure a session to run in the background, so that while the app is suspended, the system can download data on its behalf and wake up the app to deliver the results.

## 主题

### 一、第一步

Configure and create sessions, then use them to create tasks that interact with URLs.

#### ● [Fetching Website Data into Memory]()
Receive data directly into memory by creating a data task from a URL session.

#### ● [Uploading Data to a Website]()
Post data from your app to servers.

#### ● [Downloading Files in the Background]()
Create tasks that download files while your app is inactive.

#### ● [class URLSession](./URLSession/)

协调一组相关网络数据传输任务的对象。

#### ● [class URLSessionConfiguration](./URLSessionConfiguration/)

一个配置对象，用于定义URL会话的行为和策略。

#### ● [class URLSessionTask]()
A task, such as downloading a specific resource, to be undertaken by a URL session.

### 二、请求和响应

#### ● [struct URLRequest]()
A URL load request that is independent of protocol or URL scheme.

#### ● [class URLResponse]()
The metadata associated with the response to a URL load request, independent of protocol and URL scheme.

#### ● [class HTTPURLResponse]()
The metadata associated with the response to an HTTP protocol URL load request.

### 三、缓存行为

#### ● [Accessing Cached Data]()
Control how URL requests make use of previously cached data.

#### ● [class CachedURLResponse]()
A cached response to a URL request.

#### ● [class URLCache]()
An object that maps URL requests to cached response objects.

### 四、身份验证和证书

#### ● [Handling an Authentication Challenge]()
Respond appropriately when a server demands authentication for a URL request.

#### ● [class URLAuthenticationChallenge](./URLAuthenticationChallenge/)

来自需要来自客户端的认证的服务器的挑战。
A challenge from a server requiring authentication from the client.

#### ● [class URLCredential]()
An authentication credential consisting of authentication information specific to the type of credential and the type of persistent storage to use, if any.

#### ● [class URLCredentialStorage]()
An object that manages the credential storage.

#### ● [class URLProtectionSpace]()
A server or an area on a server, commonly referred to as a realm, that requires authentication.

### 五、Cookies

#### ● [class HTTPCookie]()
An object that represents an HTTP cookie. It is an immutable object, initialized from a dictionary containing the cookie attributes.

#### ● [class HTTPCookieStorage]()
A singleton object (shared instance) that manages storage of cookies.

### 六、错误

#### ● [struct URLError]()
Error codes returned by URL loading APIs.

#### ● [URL Loading System Error Info Keys]()
Recognize these keys from the user info dictionary of error objects produced by URL Loading APIs.

### 七、Legacy

#### ● [Legacy URL Loading Systems]()
Migrate your code away from using these legacy objects.

## 其他内容

### 网络

#### ● [Bonjour]()
Advertise services for easy discovery on local networks, or discover services advertised by others.