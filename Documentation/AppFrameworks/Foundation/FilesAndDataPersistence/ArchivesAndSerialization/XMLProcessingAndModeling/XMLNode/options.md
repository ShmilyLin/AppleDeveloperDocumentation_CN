# XMLNode.Options

这些常量是所有`NSXMLNode`对象（除非另有说明）的输入和输出选项，包括[XMLDocument]()对象。你可以在`NSXMLNode`方法的[init(kind:options:)]()和[xmlString(options:)]()方法中指定这些选项。

## 定义

```swift
struct Options
```

## 概述

名称中带有“保留”的选项仅在解析XML的外部源时适用。它们对以编程方式创建的节点对象没有影响。`NSXMLDocument`的初始化和输出方法中使用了其他选项。有关详细信息，请参见[XMLDocument]()参考文档。

## 主题

### 类型属性


static var documentIncludeContentTypeDeclaration: XMLNode.Options
Includes a content type declaration for HTML or XHTML in the output of the document.

static var documentTidyHTML: XMLNode.Options
Formats HTML into valid XHTML during processing of the document.

static var documentTidyXML: XMLNode.Options
Changes malformed XML into valid XML during processing of the document.

static var documentValidate: XMLNode.Options
Validates this document against its DTD (internal or external) or XML Schema.

static var documentXInclude: XMLNode.Options
Replaces all XInclude nodes in the document with the nodes referred to.

static var nodeCompactEmptyElement: XMLNode.Options
Requests that an element should be contracted when empty; for example, <flag/>.

static var nodeExpandEmptyElement: XMLNode.Options
Requests that an element should be expanded when empty; for example, <flag></flag>. This is the default.

static var nodeIsCDATA: XMLNode.Options
Specifies that a text node contains and is written out as a CDATA section.

static var nodeLoadExternalEntitiesAlways: XMLNode.Options
Requests that external entities are always loaded.

static var nodeLoadExternalEntitiesNever: XMLNode.Options
Requests that external entities are never loaded.

static var nodeLoadExternalEntitiesSameOriginOnly: XMLNode.Options
Requests that external entities are always loaded and only applies when a URL has been provided.

static var nodeNeverEscapeContents: XMLNode.Options
static var nodePreserveAll: XMLNode.Options
static var nodePreserveAttributeOrder: XMLNode.Options
Requests that NSXMLNode preserve the order of attributes as in the source XML.

static var nodePreserveCDATA: XMLNode.Options
Requests that NSXMLNode preserve CDATA blocks where defined in the input XML.

static var nodePreserveCharacterReferences: XMLNode.Options
Specifies that character references (&#nnn;) should not be resolved for XML output of this node.

static var nodePreserveDTD: XMLNode.Options
Specifies that declarations in a DTD should be preserved until it the DTD is modified. For example, parameter entities are by default expanded; with this option, they are written out as they originally occur in the DTD.

static var nodePreserveEmptyElements: XMLNode.Options
Specifies that empty elements in the input XML be preserved in their contracted or expanded form.

static var nodePreserveEntities: XMLNode.Options
Specifies that entities (&xyz;) should not be resolved for XML output of this node.

static var nodePreserveNamespaceOrder: XMLNode.Options
Requests NSXML to preserve the order of namespace URI definitions as in the source XML.

static var nodePreservePrefixes: XMLNode.Options
Requests NSXMLNode not to choose prefixes based on the closest namespace URI definition.

static var nodePreserveQuotes: XMLNode.Options
Specifies that the quoting style used in the input XML (single or double quotes) be preserved.

static var nodePreserveWhitespace: XMLNode.Options
Requests NSXMLNode to preserve whitespace characters (such as tabs and carriage returns) in the XML source that are not part of node content.

static var nodePrettyPrint: XMLNode.Options
Print this node with extra space for readability. (Output)

static var nodePromoteSignificantWhitespace: XMLNode.Options
static var nodeUseDoubleQuotes: XMLNode.Options
Requests that NSXML use double quotes for the value of an attribute or namespace node. This is the default.

static var nodeUseSingleQuotes: XMLNode.Options
Requests that NSXML use single quotes for the value of an attribute or namespace node.