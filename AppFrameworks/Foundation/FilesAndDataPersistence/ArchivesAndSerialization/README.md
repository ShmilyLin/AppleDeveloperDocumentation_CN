# Archives and Serialization

在属性列表、JSON和其他平面二进制表示形式之间来回转换对象和值。

## 主题

### 第一步

* [Encoding and Decoding Custom Types]()
Make your data types encodable and decodable for compatibility with external representations such as JSON.

* [typealias Codable]()
A type that can convert itself into and out of an external representation.

* [protocol NSCoding]()
A protocol that enables an object to be encoded and decoded for archiving and distribution.

* [protocol NSSecureCoding]()
A protocol that enables encoding and decoding in a manner that is robust against object substitution attacks.

### JSON

* [Using JSON with Custom Types]()
Demonstrates approaches for encoding and decoding different kinds of JSON in Swift.

* [class JSONEncoder]()
An object that encodes instances of a data type as JSON objects.

* [class JSONDecoder]()
An object that decodes instances of a data type from JSON objects.

* [class JSONSerialization]()
An object that converts between JSON and the equivalent Foundation objects.

### 属性列表

* [class PropertyListEncoder]()
An object that encodes instances of data types to a property list.

* [class PropertyListDecoder]()
An object that decodes instances of data types from a property list.

* [class PropertyListSerialization]()
An object that converts between a property list and one of several serialized representations.

### XML

* [XML处理与模型化](./XMLProcessingAndModeling/)

    解析XML文档。

### Keyed Archivers

* [class NSKeyedArchiver]()
An encoder that stores an object’s data to an archive referenced by keys.

* [protocol NSKeyedArchiverDelegate]()
The optional methods implemented by the delegate of a keyed archiver.

* [class NSKeyedUnarchiver]()
A decoder that restores data from an archive referenced by keys.

* [protocol NSKeyedUnarchiverDelegate]()
The optional methods implemented by the delegate of a keyed unarchiver.

* [class NSCoder]()
An abstract class that serves as the basis for objects that enable archiving and distribution of other objects.

