# canonicalRequest(for:)

返回一个指定请求的规范版本。

---
## 声明

```swift
class func canonicalRequest(for request: URLRequest) -> URLRequest
```

## 参数

* **request**

  想要获得其规范版本的请求。

## 返回值

`request`的规范格式。

## 说明

每个具体的协议实现都要定义什么是“规范”。协议应该保证相同的输入请求总是产生相同的规范形式。

实现此方法时应特别考虑，因为请求的规范形式用于在URL缓存中查找对象，这是一个在`NSURLRequest`对象之间执行相等性检查的过程。

这是一个抽象方法，子类必须提供一个实现。

