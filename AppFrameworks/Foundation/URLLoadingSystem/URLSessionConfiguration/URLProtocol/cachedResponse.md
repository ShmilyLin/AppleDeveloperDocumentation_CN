# cachedResponse

协议的缓存响应。

---
## 声明

```swift
@NSCopying var cachedResponse: CachedURLResponse? { get }
```

## 说明

如果未在子类中重写，则此方法返回在初始化时存储的缓存响应。

---
## 其他内容


### 获取协议属性

#### ● [var client: URLProtocolClient?](./client.md)

协议用来与URL加载系统进行通信的对象。

#### ● [var request: URLRequest](./request.md)

协议的请求。

#### ● [var task: URLSessionTask?](./task.md)

协议的任务。