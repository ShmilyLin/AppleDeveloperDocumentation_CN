# registerClass(_: )

尝试注册`NSURLProtocol`的子类，使其对URL加载系统可见。

---
## 声明

```swift
class func registerClass(_ protocolClass: AnyClass) -> Bool
```

## 参数

* **protocolClass**

  要注册的`NSURLProtocol`子类。

## 返回值

如果注册成功则返回`true`，否则返回`false`。 唯一的失败条件是`protocolClass`不是`NSURLProtocol`的子类。

## 说明

当URL加载系统开始加载请求时，会依次查询每个注册的协议类，以查看它是否可以使用指定的请求进行初始化。第一个在[canInit(with:)](./canInit-with.md)方法中返回`true`的`NSURLProtocol`子类将用于执行URL加载。无法保证所有注册的协议类都被查询到。

类将与注册相反的顺序进行查询遍历。一个类似的管理流程设计是使用[canonicalRequest(for:)](./canonicalRequest-for.md)创建规范形式的请求。

---
## 其他内容

### 注册和取消注册协议类

#### ● [class func unregisterClass(AnyClass)](./unregisterClass.md)

取消注册指定的`NSURLProtocol`的子类。