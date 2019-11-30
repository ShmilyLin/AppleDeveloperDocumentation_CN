# unregisterClass(_: )

取消注册指定的`NSURLProtocol`的子类。

---
## 声明

```swift
class func unregisterClass(_ protocolClass: AnyClass)
```

## 参数

* **protocolClass**

  要取消注册的`NSURLProtocol`子类。

## 说明

在调用此方法后，URL加载系统不再查询`protocolClass`对应的类。

---

## 其他内容

### 注册和取消注册协议类

#### ● [class func registerClass(AnyClass)](./registerClass.md)

尝试注册`NSURLProtocol`的子类，使其对URL加载系统可见。
