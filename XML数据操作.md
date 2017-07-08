# Uniyt3D-

## 创建XmlDocument
XmlDocument文件可以通过两种方式进行创建:
* 加载xml文件
* 通过字符串变量的形式

### 1. 加载xml文件

有以下XML文档data.xml.

```
<root>
  <data>
      <student id="1">
        <name>张三</name>
        <age>20</age>
      </student>
      <student id="2">
        <name>李四</name>
        <age>30</age>
      </student>
  </data>
</root>
```

当此文件放置在Assets目录下，加载代码如下
```
XmlDocument doc = new XmlDocument();
doc.Load(Application.dataPath + @"/data.xml");
```

### 2.通过字符串变量的形式创建XmlDocument
XmlDocument doc = new XmlDocument();
string xmldata ="<root><data><student id='1'><name>张三</name><age>20</age></student><student id = '2'><name>李四</name><age>30</age></student></data></root>";
doc.LoadXml(xmldata);

## XML处理预备知识
在整个XML处理过中，需要使用到的几个类的关系图:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/XML%E7%BC%96%E5%86%99%E8%A7%84%E8%8C%83/XML%E6%95%B0%E6%8D%AE%E6%93%8D%E4%BD%9C/images/20161205175000.jpg)

* 1 XMLElement 主要是针对节点的一些属性进行操作
* 2 XMLDocument 主要是针对节点的CUID操作
* 3 XMLNode 为抽象类，做为以上两类的基类，提供一些操作节点的方法

## 获取XML根元素

```
XmlDocument doc = new XmlDocument();
doc.Load(Application.dataPath + @"/data.xml");

//获取到根元素
XmlElement root = doc.DocumentElement;
```

## 选取的结点

关于结点的选取常用的方法有以下两种:
* SelectSingleNode 用于获取单个结点
* SelectNodes 用于获取多个同名结点

假设我们想获取所有student的信息,那必须要先访问到data结点，此时需要使用的方法是XmlElement.__SelectSingleNode__(结点标记名)

```
//选定students结点
XmlNode data = root.SelectSingleNode("data");
```

当获取到data结点后，才能对所有的student信息进行访问。对于多个同名元素的访问，需要使用XmlNode.__SelectNodes__(结点名)
```
XmlNodeList list=data.SelectNodes("student");
```
如果多个元素不同名，可以通过获取单个结点的方式单独访问，或者直接使用XmlNode.__ChildNodes__ 属性来获取所有的子结点。

```
XmlNodeList list=data.ChildNodes;
```

## 元素及属性访问

### 1.获取元素.

【案例1】获取李四的年龄
```
//获取李四的年龄
XmlNode node = list[1].SelectSingleNode("age");
//输出此结点的xml内容
print(node.OuterXml);
//只获取age标签内的文本
print(node.InnerText);
```

### 2. 获取修改属性

对于属性的获取，可以使用以下方式:
* XmlElement的GetAttribute方法
* XmlNode的Attributes属性数组

```
//获取李四的序号
XmlNode node2 = list[1];
//将结点转为XmlElement
XmlElement xl = (XmlElement)node2;
//通过GetAttribute方法
print(xl.GetAttribute("id"));
//通过SetAttribute方法修改属性
xl.SetAttribute("id", "2");
//通过属性方式
print(node2.Attributes[0].Value);
```

## 数据操作案例

### XML创建,添加，更新，删除内容

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/XML%E7%BC%96%E5%86%99%E8%A7%84%E8%8C%83/XML%E6%95%B0%E6%8D%AE%E6%93%8D%E4%BD%9C%E5%8F%8A%E5%BA%8F%E5%88%97%E5%8C%96%E5%92%8C%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96/images/Image6.png)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/XML%E7%BC%96%E5%86%99%E8%A7%84%E8%8C%83/XML%E6%95%B0%E6%8D%AE%E6%93%8D%E4%BD%9C%E5%8F%8A%E5%BA%8F%E5%88%97%E5%8C%96%E5%92%8C%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96/images/Image1.png)

点击CrateXml会在Assets路径中创建一个Xml文件，并且写入相应内容所上图所示。
添加示例代码如下：

```c#
using UnityEngine;
using System.Collections;
using System.Xml;

public class CreatXml : MonoBehaviour {

	void Start () {

	}
    void OnGUI()
    {
        if(GUI.Button(new Rect(0,10,100,30),"Creat"))
        {
            XmlDocument doc = new XmlDocument();
            XmlElement bookstore = doc.CreateElement("bookstore");       //创建根节点

            Creatxml(doc,bookstore,new XmlElement[5], new string[] { "book", "title", "auther", "year", "price" },
                                               new string[] { "悬疑", "CN", "盗墓笔记", "南派三叔", "2005", "198" });
        }
        if(GUI.Button(new Rect(0,50,100,30),"Add"))
        {
            XmlDocument doc = new XmlDocument();
            doc.Load(Application.dataPath + "/book.xml");
            XmlElement bookstore = doc.DocumentElement;                  //读取xml文档里的根节点
            Creatxml(doc, bookstore, new XmlElement[5], new string[] { "book", "title", "auther", "year", "price" },
                                               new string[] { "四大名著", "CN", "西游记", "南派三叔", "2005", "198" });
        }
        if(GUI.Button(new Rect(0,90,100,30),"Delete"))
        {
            XmlDocument doc = new XmlDocument();
            doc.Load(Application.dataPath + "/book.xml");
            XmlElement book = doc.DocumentElement.FirstChild as XmlElement;   //获取book节点
            XmlNodeList bookchild = book.ChildNodes;                         //获取book的子节点
            for (int i = 0; i < bookchild.Count; i++)
            {
                if(bookchild[i].Name == "title")
                {
                    book.RemoveChild(bookchild[i]);                         //删除book节点的title子节点
                }
            }
            doc.Save(Application.dataPath + "/book.xml");
        }
        if(GUI.Button(new Rect(0,130,100,30), "Update"))
        {
            XmlDocument doc = new XmlDocument();
            doc.Load(Application.dataPath + "/book.xml");
            XmlElement book = doc.DocumentElement.FirstChild as XmlElement;   //获取book节点
            XmlNodeList bookchild = book.ChildNodes;                         //获取book的子节点
            for (int i = 0; i < bookchild.Count; i++)
            {
                if (bookchild[i].Name == "auther")
                {
                    bookchild[i].InnerText = "董俊峰";                        //更改auther的内容      
                }
            }
            doc.Save(Application.dataPath + "/book.xml");
        }
    }
    
	void Creatxml(XmlDocument doc,XmlElement bookstore, XmlElement[] xml,string[] element, string[] text)
    {
        //XmlDocument doc = new XmlDocument();

        //XmlElement bookstore = doc.CreateElement("bookstore");
        //XmlElement book = doc.CreateElement("book");
        //XmlElement title = doc.CreateElement("title");
        //XmlElement auther = doc.CreateElement("auther");
        //XmlElement year = doc.CreateElement("year");
        //XmlElement price = doc.CreateElement("price");

        //book.SetAttribute("category", "悬疑");
        //title.SetAttribute("lang", "ch");
        //title.InnerText = "盗墓笔记";
        //auther.InnerText = "南派三叔";
        //year.InnerText = "2004";
        //price.InnerText = "25";

        //book.AppendChild(title);
        //book.AppendChild(auther);
        //book.AppendChild(year);
        //book.AppendChild(price);
        //bookstore.AppendChild(book);
        //doc.AppendChild(bookstore);
        for (int i = 0; i < xml.Length; i++)
        {
            xml[i] = doc.CreateElement(element[i]);           //创建节点
        }
        xml[0].SetAttribute("category", text[0]);             //添加属性
        xml[1].SetAttribute("lang", text[1]);
        for (int i = 1; i < xml.Length; i++)
        {
            xml[i].InnerText = text[i+1];                    //添加节点内容
            xml[0].AppendChild(xml[i]);                      //将book的子节点放入book子类中
        }
        bookstore.AppendChild(xml[0]);
        doc.AppendChild(bookstore);

        doc.Save(Application.dataPath + "/book.xml");     
    }
	
}
```


















