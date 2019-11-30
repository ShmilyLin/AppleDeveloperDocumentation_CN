# client

协议用来与URL加载系统进行通信的对象。

---
## 声明

```swift
var client: URLProtocolClient? { get }
```

---
## 其他内容

### 获取协议属性

#### ● [var cachedResponse: CachedURLResponse?](./cachedResponse.md)

协议的缓存响应。

#### ● [var request: URLRequest](./request.md)

协议的请求。

#### ● [var task: URLSessionTask?](./task.md)

协议的任务。