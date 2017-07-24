# Uniyt3D-Protobuf
## Protobuf简介

### Protocol Buffers定义:

Protocol Buffers是 Google公司开发的一种 数据描述语言，类似于 XML能够将结构化数据序列化，可用于数据存储、 通信协议等方面。它不依赖于语言和平台并且可扩展性极强。现阶段官方支持C++、JAVA、Python等三种编程语言，但可以找到大量的几乎涵盖所有语言的第三方拓展包。

protobuf-net地址：https://github.com/mgravell/protobuf-net

## Protobuf优点

### 为什么不只用XML？

同XML相比，Protocol buffers在序列化结构化数据方面有许多优点：
* 1.更简单

* 2.数据描述文件只需原来的1/10至1/3

* 3.解析速度是原来的20倍至100倍

* 4.减少了二义性

* 5.生成了更容易在 编程中使用的数据访问类

* 6.支持多种编程语言

## Protobuf性能分析

如下列图所示，Protobuf性能相对较好，应用领域包括：网络传输，配置文件，数据存储等

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Protobuf/images/Image.png)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Protobuf/images/Image1.png)

## Protobuf语法规则

### 指定字段类型

所有的字段都是标量类型：string、bool类型、int类型等等，当然，你也可以为字段指定其他的合成类型，包括枚举（enumerations）或其他消息类型。

### 分配标识号

在消息定义中，每个字段都有唯一的一个标识符。这些标识符是用来在消息的二进制格式中识别各个字段的，一旦开始使用就不能够再改。

* 注：[1,15]之内的标识号在编码的时候会占用一个字节。[16,2047]之内的标识号则占用2个字节。所以应该为那些频繁出现的消息元素保留 [1,15]之内的标识号

* 切记：要为将来有可能添加的、频繁出现的标识号预留一些标识号。
最小的标识号可以从1开始，最大到229 - 1, or 536,870,911。不可以使用其中的[19000－19999]的标识号， Protobuf协议实现中对这些进行了预留。如果非要在.proto文件中使用这些预留标识号，编译时就会报警。

### 指定字段规则

所指定的消息字段修饰符必须是如下之一：
* required：不可增加或删除的字段，必须初始化；
* optional：可选字段，可删除，可以不初始化；
* repeated：可重复字段(对应C#里面的List)。

### 标量数值类型
一个标量消息字段可以含有一个如下的类型——该表格展示了定义于.proto文件中的类型，以及与之对应的、在自动生成的访问类中定义的类型：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Protobuf/images/Image3.png)

### 添加注释

向.proto文件添加注释，也跟C#语法一样(//)的语法格式，如：

```cs
message SearchRequest
{
    required string query =1;
    optional int32 page_number =2; //最终返回的页数
    optional int32 result_per_page =3; //每页返回的结果数   
}
```

### 枚举类型
```c#
message SearchRequest
{
    required string query = 1;
    optional int32 page_number = 2;
    optional int32 result_per_page = 3 [default = 10];
    enum Corpus {
    UNIVERSAL = 0;
    WEB = 1;
    IMAGES = 2;
    LOCAL = 3;
    NEWS = 4;
    PRODUCTS = 5;
    VIDEO = 6;
}
optional Corpus corpus = 4 [default = UNIVERSAL];
}
```
### 嵌套类型
```c#
package Cmd;
	message Person
	{
	    message Address
	    {
	         required string Line1 = 1;
	         required string Line2 = 2;
	    }
    	required int32 Id = 1;
	    required string Name = 2;
	    required Address address = 3;
  }
```

### 多重嵌套

```c#
package Cmd;
message Outer {
  message MiddleAA{
    message Inner {
      required int64 ival = 1;
      optional bool  booly = 2;
    }
  }
  message MiddleBB {
    message Inner {
      required int32 ival = 1;
      optional bool  booly = 2;
    }
  }
}
```
### 引用外部定义的消息类型
```c#
UserData.proto
	message UserItem
	{
		required string userId = 1;
		required string userName = 2;
	}
Test.proto
	package Cmd;
	import "UserData.proto";
	message Test
	{
		optional string name = 1;
		required UserItem userItem = 2;
	}
```

## Protobuf例子

protobuf应用于C#Model的实际案例，代码如下所示：
```cs
Package Cmd;
message Person
{
	optional string Child = 1;
	repeated string Parent = 2;
	required string Name = 3;
	required bool Gender = 4;
	required string Msg = 5;
}
```
紧接着将Protobuf格式的文件转化成我们熟知C#的Model，
步骤如下：

首先打开cmd控制台，然后将下载好的protogen.exe拖进去，然后空格加-i：，然后把需要转换的.Proto格式的文件拖进去，然后空格加-o：，再将该文件拖进去，改后缀.cs，然后回车
就会在你的当前文件夹内生成该文件的.cs文件
效果如图：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Protobuf/images/Image2.png)

## protobuf序列化和反序列化

### protobuf序列化
是指将结构化的数据按一定的编码规范转成指定格式的过程
### protobuf反序列化
是指将转成指定格式的数据解析成原始的结构化数据的过程
### 控制台演示序列化和反序列化的案例
首先创建一个Person类,然后再vs中添加引用protobuf-net.dll文件，代码如下：
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ProtoBuf;

namespace ProtolDemo
{
    [ProtoContract]           //序列化对象
    class Person
    {
        [ProtoMember(1)]      //标识符
        public string name;
        [ProtoMember(2)]
        public int age;
        [ProtoMember(3)]
        public int weight;
    }
}
```
然后封装ProtobufHelper（代码如下）类进行序列化和反序列化

```c#
using System.IO;
using System.Text;
using ProtoBuf;
namespace protobuf_test
{
    class ProtobufHelper
    {
        /// <summary>
        /// 序列化成string
        /// </summary>
        /// <typeparam name="T"></typeparam>
        /// <param name="t"></param>
        /// <returns>返回字符串</returns>
        public static string Serialize<T>(T t)
        {
            using (MemoryStream ms = new MemoryStream())
            {
                Serializer.Serialize<T>(ms, t);
                return Encoding.UTF8.GetString(ms.ToArray());
            }
        }
        /// <summary>
        /// 序列化到文件
        /// </summary>
        /// <typeparam name="T"></typeparam>
        /// <param name="path"></param>
        /// <param name="data"></param>
        public static void Serialize<T>(string path, T data)
        {
            using (Stream file = File.Create(path))
            {
                Serializer.Serialize<T>(file, data);
                file.Close();
            }
        }
        /// <summary>
        /// 根据字符串反序列化成对象
        /// </summary>
        /// <typeparam name="T"></typeparam>
        /// <param name="content"></param>
        /// <returns></returns>
        public static T DeSerialize<T>(string content)
        {
            using (MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(content)))
            {
                T t = Serializer.Deserialize<T>(ms);
                return t;
            }
        }
        /// <summary>
        /// 根据文件流返回对象
        /// </summary>
        /// <typeparam name="T"></typeparam>
        /// <param name="filestream"></param>
        /// <returns></returns>
        public static T DeSerialize<T>(Stream filestream)
        {
            return Serializer.Deserialize<T>(filestream);
        }

    }
}
```

然后在vs中代码如下：

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.IO;
using ProtoBuf;

namespace ProtolDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            Person p1 = new Person() {name = "旺财",age = 1,weight = 55};
            Person p3 = new Person() { name = "黑胖", age = 4, weight = 123 };
            
            //string P1str = ProtobufHelper.Serialize(p1);   //序列化单个对象p1；
            //Console.WriteLine(P1str);
            //Person p2 = ProtobufHelper.DeSerialize<Person>(P1str);   // 反序列化字符串P1str转换为Person类型对象
            //Console.WriteLine(p2.name + "," + p2.age + "," + p2.weight);

            List<Person> persons = new List<Person>(){p1,p3};     //将对象添加进集合
            string personstr = ProtobufHelper.Serialize(persons);   //序列化集合
            Console.WriteLine(personstr);
            List<Person> personlist = ProtobufHelper.DeSerialize<List<Person>>(personstr);   //反序列化集合
            foreach (var person in personlist)
            {
                Console.WriteLine(person.name +","+ person.age +","+ person.weight);  //遍历打印集合的内容
            }
            Console.ReadKey();
        }
    }
}
```

## Unity中使用Protobuf序列化和反序列化

* 1.首先创建一个Person.proto的文件，添加内容如下
```c#
package cmd;

message Person
{
	required string name =1;
	optional int32 age = 2;
	optional int32 weight = 3;
}
```

* 2.将该文件转换为.cs文件，拖入到Unity中，如下所示
```c#
namespace cmd
{
  [global::System.Serializable, global::ProtoBuf.ProtoContract(Name=@"Person")]
  public partial class Person : global::ProtoBuf.IExtensible
  {
    public Person() {}
    
    private string _name;
    [global::ProtoBuf.ProtoMember(1, IsRequired = true, Name=@"name", DataFormat = global::ProtoBuf.DataFormat.Default)]
    public string name
    {
      get { return _name; }
      set { _name = value; }
    }
    private int _age = default(int);
    [global::ProtoBuf.ProtoMember(2, IsRequired = false, Name=@"age", DataFormat = global::ProtoBuf.DataFormat.TwosComplement)]
    [global::System.ComponentModel.DefaultValue(default(int))]
    public int age
    {
      get { return _age; }
      set { _age = value; }
    }
    private int _weight = default(int);
    [global::ProtoBuf.ProtoMember(3, IsRequired = false, Name=@"weight", DataFormat = global::ProtoBuf.DataFormat.TwosComplement)]
    [global::System.ComponentModel.DefaultValue(default(int))]
    public int weight
    {
      get { return _weight; }
      set { _weight = value; }
    }
    private global::ProtoBuf.IExtension extensionObject;
    global::ProtoBuf.IExtension global::ProtoBuf.IExtensible.GetExtensionObject(bool createIfMissing)
      { return global::ProtoBuf.Extensible.GetExtensionObject(ref extensionObject, createIfMissing); }
  }
  
}
```
* 3.将protobuf-net.dll插件导入到Unity的Plugins中，然后将上述的ProtobufHelper脚本拖入到Unity中
* 4.完成Unity中代码，如下：
```c#
using UnityEngine;
using System.Collections;
using System.Collections.Generic;
using System.IO;
using ProtoBuf;
using cmd;
using ProtolDemo;

public class ProtobufDeme : MonoBehaviour {

    public string path = "D://PersonData";

	void Start()
    {
        Person t1 = new Person() { name = "小红", age = 15,weight = 150};
        Person t2 = new Person() { name = "小明", age = 20, weight = 120};

        List<Person> tests = new List<Person>() { t1, t2 };
        Debug.Log("序列化");
        ProtobufHelper.Serialize(path, tests);
        Debug.Log("反序列化");
        List<Person> test1 = null;
        using (Stream file = File.OpenRead(path))
        {
            test1 = ProtobufHelper.DeSerialize < List<Person>>(file);
        }
        foreach (var item in test1)
        {
            Debug.Log(item.name + "," + item.age + "," + item.weight);
        }
    }
}
```

* 5.完成序列化和反序列化，并且在 path = "D://PersonData"中生成了一个PersonData.proto的文件











