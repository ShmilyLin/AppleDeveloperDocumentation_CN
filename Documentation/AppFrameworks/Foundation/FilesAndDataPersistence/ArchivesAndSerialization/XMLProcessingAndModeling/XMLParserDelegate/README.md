# XMLParserDelegate

XML解析器用来通知其代理对象有关解析文档内容的接口。

## 定义

```swift
protocol XMLParserDelegate
```

## 主题

### 处理XML

* [func parserDidStartDocument(XMLParser)]()

    解析器对象在开始解析文档时将其发送给委托。

* [func parserDidEndDocument(XMLParser)]()

    成功完成解析后，解析器对象将其发送给委托。

* [func parser(XMLParser, didStartElement: String, namespaceURI: String?, qualifiedName: String?, attributes: [String : String])]()

    当解析器对象遇到给定元素的开始标记时，由其发送给它的委托。

* [func parser(XMLParser, didEndElement: String, namespaceURI: String?, qualifiedName: String?)]()

    当解析器对象遇到特定元素的结束标记时，由其发送给其委托。

* [func parser(XMLParser, didStartMappingPrefix: String, toURI: String)]()

    解析器对象在第一次遇到给定名称空间前缀时将其发送给其委托，该名称空间前缀已映射到URI。

* [func parser(XMLParser, didEndMappingPrefix: String)]()

    当给定的名称空间前缀超出范围时，由解析器对象发送给其委托。

* [func parser(XMLParser, resolveExternalEntityName: String, systemID: String?) -> Data?]()

    当解析器对象遇到具有特定系统ID的给定外部实体时，由解析器对象发送给其委托。

* [func parser(XMLParser, parseErrorOccurred: Error)]()

    遇到致命错误时，由解析器对象发送给其委托。

* [func parser(XMLParser, validationErrorOccurred: Error)]()

    解析器对象在遇到致命验证错误时发送给它的委托。 NSXMLParser当前不调用此方法，并且不执行验证。

* [func parser(XMLParser, foundCharacters: String)]()

    由解析器对象发送，以为其委托提供代表当前元素的全部或部分字符的字符串。

* [func parser(XMLParser, foundIgnorableWhitespace: String)]()

    由解析器对象报告，以为其委托提供一个字符串，该字符串表示当前元素的全部或部分可忽略的空白字符。

* [func parser(XMLParser, foundProcessingInstructionWithTarget: String, data: String?)]()

    解析器对象在遇到处理指令时发送给它的委托。

* [func parser(XMLParser, foundComment: String)]()

    解析器对象在XML中遇到注释时，将其发送给其委托。

* [func parser(XMLParser, foundCDATA: Data)]()

    解析器对象在遇到CDATA块时发送给它的委托。

## 处理DTD

* [func parser(XMLParser, foundAttributeDeclarationWithName: String, forElement: String, type: String?, defaultValue: String?)]()
Sent by a parser object to its delegate when it encounters a declaration of an attribute that is associated with a specific element.

* [func parser(XMLParser, foundElementDeclarationWithName: String, model: String)]()
Sent by a parser object to its delegate when it encounters a declaration of an element with a given model.

* [func parser(XMLParser, foundExternalEntityDeclarationWithName: String, publicID: String?, systemID: String?)]()
Sent by a parser object to its delegate when it encounters an external entity declaration.

* [func parser(XMLParser, foundInternalEntityDeclarationWithName: String, value: String?)]()
Sent by a parser object to the delegate when it encounters an internal entity declaration.

* [func parser(XMLParser, foundUnparsedEntityDeclarationWithName: String, publicID: String?, systemID: String?, notationName: String?)]()
Sent by a parser object to its delegate when it encounters an unparsed entity declaration.

* [func parser(XMLParser, foundNotationDeclarationWithName: String, publicID: String?, systemID: String?)]()
Sent by a parser object to its delegate when it encounters a notation declaration.