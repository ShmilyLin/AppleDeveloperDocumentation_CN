# setProperty(_:forKey:in:)

设置与指定请求中与指定key关联的属性。

---

## 声明

```swift
class func setProperty(_ value: Any, 
                    forKey key: String, 
                    in request: NSMutableURLRequest)
```

## 参数

* **value**

  要设置给指定属性的值。

* **key**

  指定属性对应的`key`。

* **request**

  指定属性所在的请求。

## 说明

此方法用于为协议实现者提供一个接口，以定制与`NSMutableURLRequest`对象关联的特定协议的信息。

---
## 其他内容

### 获取和设置请求属性

#### ● [class func property(forKey: String, in: URLRequest)](./property-forKey-in.md)

返回与指定请求中与指定key关联的属性。

#### ● [class func removeProperty(forKey: String, in: NSMutableURLRequest)](./removeProperty-forKey-in.md)

移除与指定请求中与指定key关联的属性。