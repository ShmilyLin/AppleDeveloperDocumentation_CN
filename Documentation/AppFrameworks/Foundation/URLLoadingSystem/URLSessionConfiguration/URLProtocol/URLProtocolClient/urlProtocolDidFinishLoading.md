# urlProtocolDidFinishLoading(_: )

发送给URL加载系统，表示协议实现已完成加载。

**需要**

---
## 声明

```swift
func urlProtocolDidFinishLoading(_ protocol: URLProtocol)
```

## 参数

* **protocol**

  发送消息的URL协议对象。

---
## 其他内容

### 协议方法

#### ● [func urlProtocol(URLProtocol, cachedResponseIsValid: CachedURLResponse)](./urlProtocol-cachedResponseIsValid.md)**【需要】**

发送给URL加载系统，表示这个缓存响应是有效的。

#### ● [func urlProtocol(URLProtocol, didCancel: URLAuthenticationChallenge)](./urlProtocol-didCancel.md)**【需要】**

发送给URL加载系统，表示验证质询已被取消。

#### ● [func urlProtocol(URLProtocol, didFailWithError: Error)](./urlProtocol-didFailWithError.md)**【需要】**

当加载请求由于错误而失败时发送。

#### ● [func urlProtocol(URLProtocol, didLoad: Data)](./urlProtocol-didLoad.md)**【需要】**

`NSURLProtocol`子类实例——`protocol`——在加载数据时将此消息发送给`[protocol client]`。

#### ● [func urlProtocol(URLProtocol, didReceive: URLAuthenticationChallenge)](./urlProtocol-didReceive.md)**【需要】**

发送给URL加载系统，表示已收到验证质询。

#### ● [func urlProtocol(URLProtocol, didReceive: URLResponse, cacheStoragePolicy: URLCache.StoragePolicy)](./urlProtocol-didReceive-cacheStoragePolicy.md)**【需要】**

发送给URL加载系统，表示协议实现已为请求创建响应对象。

#### ● [func urlProtocol(URLProtocol, wasRedirectedTo: URLRequest, redirectResponse: URLResponse)](./urlProtocol-wasRedirectedTo-redirectResponse.md)**【需要】**

发送给URL加载系统，表示协议实现已被重定向。