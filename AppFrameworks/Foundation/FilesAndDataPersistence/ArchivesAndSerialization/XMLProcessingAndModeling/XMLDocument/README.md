# XMLDocument

内置到逻辑树型结构中的XML文档。

## 定义

```swift
class XMLDocument : XMLNode
```

## 概述

一个XMLDocument对象可以有多个子节点，但只能有一个元素，即根元素。任何其他节点都必须是表示注释或处理指令的XMLNode对象。如果尝试将任何其他类型的子节点添加到XMLDocument对象，例如属性，名称空间，另一个文档对象或除根之外的其他元素，则XMLDocument会引发异常。如果添加有效的子节点并且该对象已经具有父节点，则XMLDocument会引发异常。 XMLDocument对象还可以具有文档全局属性，例如XML版本，字符编码，引用的DTD和MIME类型。

XMLDocument类的初始化程序读取XML的外部源（无论是本地文件还是远程网站），将其解析并将其处理为树表示形式。您还可以以编程方式构造XMLDocument。有用于获取和设置文档属性的访问器方法，使用XSLT转换文档的方法，用于动态验证文档的方法以及用于将XMLDocument的内容打印为XML，XHTML，HTML或纯文本的方法。

只要任何给定实例仅在一个线程中使用，XMLDocument类都是线程安全的。