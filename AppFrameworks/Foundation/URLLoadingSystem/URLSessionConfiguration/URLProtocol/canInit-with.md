# canInit(with:)

返回协议子类是否可以处理指定的请求。

---
## 声明

```swift
class func canInit(with request: URLRequest) -> Bool
```

## 参数

* **request**

  将要被处理的请求。

## 返回值

如果协议子类可以处理请求，则为`true`，否则为`false`。

## 说明

子类应检查`request`并确定该实现是否可以执行该请求的加载。

这是一个抽象方法，子类必须提供一个实现。

---
## 其他内容

### 确定子类是否可以处理请求

#### ● [class func canInit(with: URLSessionTask)](./canInit-with-1.md)

返回协议子类是否可以处理指定的任务。