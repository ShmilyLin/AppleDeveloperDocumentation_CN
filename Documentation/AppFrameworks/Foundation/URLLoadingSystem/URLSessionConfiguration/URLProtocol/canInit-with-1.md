# canInit(with:)

返回协议子类是否可以处理指定的任务。

---
## 声明

```swift
class func canInit(with task: URLSessionTask) -> Bool
```

## 说明

子类应检查`request`并确定实现是否可以执行该任务的加载。

这是一个抽象方法，子类必须提供一个实现。

---
## 其他内容

### 确定子类是否可以处理请求

#### ● [class func canInit(with: URLRequest)](./canInit-with.md)

返回协议子类是否可以处理指定的请求。