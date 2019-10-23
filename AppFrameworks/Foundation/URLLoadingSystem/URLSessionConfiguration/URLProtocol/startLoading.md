# startLoading()

开始特定协议的请求加载。

---
## 声明

```swift
func startLoading()
```

## 说明

当这个方法被调用时，子类实现应该开始加载请求，通过`NSURLProtocolClient`协议向URL加载系统提供反馈。

子类必须实现此方法。

---
## 其他内容

### 开始和停止下载

#### ● [func stopLoading()](./stopLoading.md)

停止特定协议的请求加载。