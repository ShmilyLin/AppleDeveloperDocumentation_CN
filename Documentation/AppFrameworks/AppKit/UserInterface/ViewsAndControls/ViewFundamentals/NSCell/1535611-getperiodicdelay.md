# getPeriodicDelay(_:interval:)



## 定义

```swift
func getPeriodicDelay(_ delay: UnsafeMutablePointer<Float>, 
             interval: UnsafeMutablePointer<Float>)
```

## 参数

* **delay**

    输入时，指向浮点变量的指针。输出时，变量包含发送消息之前的当前延迟（以秒为单位）。此参数不能为`nil`。

* **interval**

    输入时，指向浮点变量的指针。输出时，该变量包含发送消息的间隔（以秒为单位）。此参数不能为`nil`。

## 说明

默认实现返回0.2的延迟和0.025秒的间隔。子类可以重写此方法以提供自己的延迟和间隔值。