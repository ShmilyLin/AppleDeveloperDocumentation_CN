# delegate

　　App的delegate对象

---
## 声明

```swift
weak var delegate: NSApplicationDelegate? { get set }
```

---
## 说明

　　app对象和app的delegate协同工作以管理应用程序的整体行为。通常，delegate由Xcode项目模板自动配置。

---
## 其他内容

### 管理App的行为

#### ● [protocol NSApplicationDelegate](./NSApplicationDelegate/)

　　`NSApplication`的delegate对象可以实现的一组方法。