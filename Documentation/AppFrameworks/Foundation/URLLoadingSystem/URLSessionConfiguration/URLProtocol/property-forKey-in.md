# property(forKey:in:)

返回与指定请求中与指定key关联的属性。

---
## 声明

```swift
class func property(forKey key: String, 
                    in request: URLRequest) -> Any?
```

## 参数

* **key**

  想要获取的属性的key。

* **request**

  要查询对应属性的请求。

## 返回值

  属性与`key`相关联，如果没有属性存储为`key`，则返回`nil`。

## 说明

此方法为协议实现者提供了一个接口，以访问与`NSURLRequest`对象相关的协议特定信息。

---
## 其他内容

### 获取和设置请求属性

#### ● [class func setProperty(Any, forKey: String, in: NSMutableURLRequest)](./setProperty-forKey-in.md)

设置与指定请求中与指定key关联的属性。

#### ● [class func removeProperty(forKey: String, in: NSMutableURLRequest)](./removeProperty-forKey-in.md)

移除与指定请求中与指定key关联的属性。