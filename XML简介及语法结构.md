# Uniyt3D-

## XML的起源和目的

XML是Extensible Markup Language的缩写，即可扩展标记语言。它是一种用来创建的标记的标记语言。1996年，万维网协会（或者叫W3C，http://www.w3c.org ）开始设计一种可扩展的标记语言，1998年2月，XML1.0成为了W3C的推荐标准。

使用XML标记语言可以做到数据或数据结构在任何编程语言环境下的共享。例如我们在某个计算机平台上用某种编程语言编写了一些数据或数据结构，然后用XML标记语言进行处理，那样的话，其他人就可以在其他的计算机平台上来访问这些数据或数据结构，甚至可以用其他的编程语言来操作这些数据或数据结构了。这就是XML标记语言作为一种数据交换语言存在的价值。
       
##  什么是XML?
* XML 指可扩展标记语言（EXtensible Markup Language）
* XML 是一种标记语言，很类似 HTML
* XML 的设计宗旨是传输数据，而非显示数据
* XML 标签没有被预定义。您需要自行定义标签。
* XML 被设计为具有自我描述性。
* XML 是 W3C 的推荐标准

【参考案例】
下面是 John 写给 George 的便签，存储为 XML格式数据.

```c#
<?xml version="1.0" encoding="ISO-8859-1"?>
<note>
  <to>George</to>
  <from>John</from>
  <heading>Reminder</heading>
  <body>Don't forget the meeting!</body>
</note>
```

上面的这条便签具有自我描述性。它拥有标题以及留言，同时包含了发送者和接受者的信息。
但是，这个 XML 文档仍然没有做任何事情。它仅仅是包装在 XML 标签中的纯粹的信息。我们需要编写软件或者程序，才能传送、接收和显示出这个文档。

## XML的特点

* XML 仅仅是纯文本
* 通过 XML 您可以发明自己的标签
* XML 不是对 HTML 的替代,而是对HTML的补充。

## XML和HTML的区别
XML和HTML都是用于操作数据或数据结构，在结构上大致是相同的，但它们在本质上却存在着明显的区别，它们的区别主要有以下几点:
* 语法要求不同
在HTML中不区分大小写，在XML中对大小写要求非常严格。
* 标记不同
HTML使用固有的标记，而XML没有固有标记。
* 作用不同
XML 被设计用来传输和存储数据。
HTML 被设计用来显示数据。

## XML的优势
 每种语言的产生都能完成某些特定的功能，XML作为一种标记语言也不例外。XML最大的优势在于它能对各种编程语言编写的数据进行管理，使得在任何平台下都能通过解析器来读取XML数据。它的优势可归纳为以下几点:
* 数据的搜索
在XML中可以提取文档中任何位置的数据.
* 数据的显示
XML将数据的结构和数据的显示形式分开，根据需要使数据呈现出多种显示方式。如HTML、PDF等格式。
* 数据的交换
XML标记语言的语法非常简单，可以通过解析器在任何机器上解读。并可以在各种计算机平台上使用。逐渐成为一种数据交换的语言。

## XML文档结构
XML 文档形成了一种树结构，它从“根部”开始，然后扩展到“枝叶”。

### 简单案例
XML 使用简单的具有自我描述性的语法：
```c#
<?xml version="1.0" encoding="ISO-8859-1"?>
<note>
<to>George</to>
<from>John</from>
<heading>Reminder</heading>
<body>Don't forget the meeting!</body>
</note>
```
第一行是 XML 声明。它定义 XML 的版本 (1.0) 和所使用的编码 (ISO-8859-1 = Latin-1/西欧字符集)。
下一行描述文档的根元素（像在说：“本文档是一个便签”）：
```
<note>
```

接下来 4 行描述根的 4 个子元素（to, from, heading 以及 body）：
```
<to>George</to>
<from>John</from>
<heading>Reminder</heading>
<body>Don't forget the meeting!</body>
```
最后一行定义根元素的结尾：
```
</note>
```
从本例可以设想，该 XML 文档包含了 John 给 George 的一张便签。

### XML的树形结构
XML 文档必须包含根元素。该元素是所有其他元素的父元素。
XML 文档中的元素形成了一棵文档树。这棵树从根部开始，并扩展到树的最底端。
所有元素均可拥有子元素：
```
<root>
  <child>
    <subchild>.....</subchild>
  </child>
</root>
```
父、子以及同胞等术语用于描述元素之间的关系。父元素拥有子元素。相同层级上的子元素成为同胞（兄弟或姐妹）。
所有元素均可拥有文本内容和属性（类似 HTML 中）。

### 案例分析

使用XML来表示一个书店里的图书信息.

```c#
<bookstore>
  <book category="COOKING">
    <title lang="en">Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>
  <book category="CHILDREN">
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>
  <book category="WEB">
    <title lang="en">Learning XML</title>
    <author>Erik T. Ray</author>
    <year>2003</year>
    <price>39.95</price>
  </book>
</bookstore>
```

如果使用树形的结构图去描述XMl的方式，将会得到下面的一张图.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/XML%E7%BC%96%E5%86%99%E8%A7%84%E8%8C%83/XML%E7%AE%80%E4%BB%8B/images/20161205131929.jpg)

例子中的根元素是bookstore。文档中的所有 book 元素都被包含在 bookstore 中。
book 元素有 4 个子元素：
```
<title>
<auther>
<year>
<price>
```
# XML的语法结构

## 1. XML中的注释
在 XML 中编写注释的语法与 HTML 的语法很相似：
```
<!-- This is a comment -->
```
在 XML 中，空格会被保留,HTML 会把多个连续的空格字符裁减（合并）为一个：
```
HTML:	Hello           my name is David.
输出:	Hello my name is David.
```
在 XML 中，文档中的空格不会被删节。

## 2. XML语法规则
* XML 文档必须有根元素
* 所有 XML 元素都须有关闭标签
* XML 标签对大小写敏感
* XML 必须正确地嵌套
* XML 的属性值须加引号
