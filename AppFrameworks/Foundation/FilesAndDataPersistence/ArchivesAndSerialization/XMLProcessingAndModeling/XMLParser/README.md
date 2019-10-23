# XMLParser

XML文档（包括DTD声明）的事件驱动解析器。

## 定义

```swift
class XMLParser : NSObject
```

## 概述

`XMLParser`在处理XML文档时将其遇到的项目（元素，属性，CDATA块，注释等）通知其代理对象。它本身不对那些解析的项目做任何事情，只是报告它们。它还报告解析错误。为了方便起见，以下描述中的`XMLParser`对象有时称为解析器对象。除非在回调中使用，否则XMLParser是线程安全的类，只要任何给定的实例仅在一个线程中使用即可。

> **注意**
> 
> 从macOS 10.4开始，在`XMLParser`中实现了命名空间的支持。
> 此版本之前的`XMLParser`中与命名空间相关的方法无效。

## 主题

### 初始化一个解析器对象

* [init?(contentsOf: URL)]()
Initializes a parser with the XML content referenced by the given URL.

* [init(data: Data)]()
Initializes a parser with the XML contents encapsulated in a given data object.

* [init(stream: InputStream)]()
Initializes a parser with the XML contents from the specified stream and parses it..

### 管理代理

* [var delegate: XMLParserDelegate?]()

    接收解析过程中的消息的代理对象。

### 管理解析器行为

* [var shouldProcessNamespaces: Bool](./1418380-shouldprocessnamespaces.md)

    一个布尔值，它确定解析器是否报告元素的名称空间和合格名称。

* [var shouldReportNamespacePrefixes: Bool](./1410809-shouldreportnamespaceprefixes.md)

    一个布尔值，它确定解析器是否报告表示名称空间声明范围的前缀。

* [var shouldResolveExternalEntities: Bool](./1414143-shouldresolveexternalentities.md)

    一个布尔值，它确定解析器是否报告外部实体的声明。

### 解析

* [func parse() -> Bool]()

    开始事件驱动的解析操作。

* [func abortParsing()]()

    停止解析器对象。

* [var parserError: Error?]()

    一个你可以从中获取有关解析错误信息的[NSError]()对象。

### 获取解析器状态

* [var columnNumber: Int]()

    解析器正在处理的XML文档的列号。

* [var lineNumber: Int]()

    解析器正在处理的XML文档的行号。

* [var publicID: String?]()

    XML文档中引用的外部实体的公共标识符。

* [var systemID: String?]()

    XML文档中引用的外部实体的系统标识符。

### 常量

* [enum XMLParser.ExternalEntityResolvingPolicy]()
* [class let errorDomain: String]()

    指示XML解析中的错误。

* [enum XMLParser.ErrorCode]()

    以下错误代码由`NSXMLParser`定义。有关此处未列出的错误代码，请参见`<libxml/xmlerror.h>`头文件。

### 实例属性

* [var allowedExternalEntityURLs: Set<URL>?]()
* [var externalEntityResolvingPolicy: XMLParser.ExternalEntityResolvingPolicy]()