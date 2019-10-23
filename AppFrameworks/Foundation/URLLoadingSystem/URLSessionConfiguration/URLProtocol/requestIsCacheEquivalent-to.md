# requestIsCacheEquivalent(_:to:)

返回两个请求是否有相同的`cache purposes`。

---
## 声明

```swift
class func requestIsCacheEquivalent(_ a: URLRequest, 
                                   to b: URLRequest) -> Bool
```

## 参数

* **aRequest**

  将要与`bRequest`比较的请求。

* **bRequest**

  将要与`aRequest`比较的请求。

## 返回值

如果`aRequest`和`bRequest`有相同的`cache purposes`，则为`true`，否则为`false`。只有当它们由同一个协议处理并且该协议在执行指定实现的检查之后声明它们相同时，请求才被视为有相同的`cache purposes`。

## 说明

此方法的`NSURLProtocol`本身的实现是比较请求的URL以确定请求是否应该被视为等同。子类可以覆盖此方法以提供特定协议的比较。
