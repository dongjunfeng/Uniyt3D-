# Uniyt3D-

## JSON简介
JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它基于ECMAScript的一个子集。 JSON采用完全独立于语言的文本格式，但是也使用了类似于C语言家族的习惯（包括C、C++、C#、Java、JavaScript、Perl、Python等）。这些特性使JSON成为理想的数据交换语言。 易于人阅读和编写，同时也易于机器解析和生成(一般用于提升网络传输速率)。

## JSON的语法规则

JSON 语法是 JavaScript 对象表示语法的子集。
* 数据在键值对中
* 数据由逗号分隔
* 花括号保存对象
* 方括号保存数组

## JSON 名称/值对

JSON 数据的书写格式是：名称/值对。
名称/值对组合中的名称写在前面（在双引号中），值对写在后面(同样在双引号中)，中间用冒号隔开：
```
"firstName":"John"
```
这很容易理解，等价于这条 c# 语句：
```
firstName="John"
```

## JSON基础结构
JSON结构有两种结构,这两种结构就是对象和数组两种结构，通过这两种结构可以表示各种复杂的结构。

### 1、对象

对象在js中表示为“{}”括起来的内容，数据结构为{key：value,key：value,…}的键值对的结构，在面向对象的语言中，key为对象的属性，value为对应的属性值，所以很容易理解，取值方法为 对象.key 获取属性值，这个属性值的类型可以是 数字、字符串、数组、对象几种。

【参数案例1】
使用JSON数据表示iPhone手机的一些信息。
```
{"name":"iPhone","price":3000}
```

具体形式:
对象是一个无序的“名称/值”对集合。
* （1）一个对象以“{”（左括号）开始，“}”（右括号）结束。
* （2）每个“名称”后跟一个“:”（冒号）；
* （3）“‘名称/值’ 对”之间使用“,”（逗号）分隔。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/JSON/JSON%E7%AE%80%E4%BB%8B/images/20161206174643.jpg)

例子：表示人的一个对象.

```
{
    "姓名":"大憨",
    "年龄":24
}
```

【参数案例3】
表示一个外国人的名字.

```
{"firstName":"Brett","lastName":"McLaughlin"}
```
在这组数据里，firstName和lastName是键（key），而Brett和McLaughlin是值（value）。

### 2、数组
数组在js中是中括号“[]”括起来的内容，数据结构为 [“java”,“javascript”,“vb”,…]，取值方式和所有语言中一样，使用索引获取，字段值的类型可以是 数字、字符串、数组、对象几种。

当需要表示一组值时，JSON 不但能够提高可读性，而且可以减少复杂性。如果使用 JSON，就只需将多个带花括号的记录分组在一起.

【参数案例3】
通过JSON数据存储三位外国人的名字及邮箱信息。

```c#
{
    "people":[
        {"firstName":"Brett","lastName":"McLaughlin","email":"aaa@163.com"},
        {"firstName":"Jason","lastName":"Hunter","email":"bbbb@163.com"},
        {"firstName":"Elliotte","lastName":"Harold","email":"cccc@163.com"}
    ]
}
```
具体形式
数组是值（value）的有序集合
* （1）一个数组以“[”（左中括号）开始，“]”（右中括号）结束。
* （2）值之间使用“,”（逗号）分隔。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/JSON/JSON%E7%AE%80%E4%BB%8B/images/20161206174805.jpg)

例子：一组学生

```c#
{
    "学生": [
        {"姓名":"小明","年龄":23},
        {"姓名":"大憨","年龄":24}
    ]
}
```
说明：此Json对象包括了一个学生数组，而学生数组中的值又是两个Json对象。

# LitJson解析JSON

## 常用Json库简介
不推荐
* Json.NET .NET自带的JSON库，缺点：比较臃肿
* MiniJson 缺点：不支持自定义的序列化
* LitJson 缺点：IOS平台支持不太友好,只做Android平台可以考虑使用

推荐
* MyJson
https://github.com/lightszero/myjson
* SimpleJson
http://blog.csdn.net/kakashi8841/article/details/21877131

强烈推荐
* JsonFX

## 1. LitJson配置

将库脚本或动态库(LitJSON.dll)置在Assets目录下的Plugins文件夹中，因为plugins文件夹中的脚本会先运行。

## 2.JSON的生成
(1) 使用JsonData生成普通JOSN
```c#
      JsonData data=new JsonData();
      data["name"] = "zhansan";
      data["age"] = 28;
      data["sex"] ="male";
      string  json1= data.ToJson();
      Debug.Log(json1);

      ---------------运行结果-----------------
      {"name":"zhansan","age":28,"sex":"male"} 
```
(2) 使用JsonData生成嵌套结构JSON

```c#
JsonData data2 = new JsonData();
        data2["name"] = "zhansan";
        data2["info"] = new JsonData();
        data2["info"]["sex"] = "male";
        data2["info"]["age"] = 28;
		string  json2 = data2.ToJson();
        Debug.Log(json2);

        ---------------运行结果-----------------
      {"name":"zhansan","info":{"sex":"male","age":28}}   
```
(3) 使用 JsonMapper生成JSON

【Payer.cs】
```c#
using System.Collections;
public class Player {
    public string name { get; set; }
    public int age { get; set; }
    public string sex { get; set; }
}
```
将Player对象转为Json格式
```c#
Player player = new Player();
    player.name = "peiandsky";
    player.age = 23;
    player.sex = "male";
    string json=JsonMapper.ToJson(player);
```

## 使用JsonWritter生成JSON

1)对象类型json
```c#
JsonWriter writer = new JsonWriter();
    writer.WriteObjectStart ();
    writer.WritePropertyName("name");
    writer.Write("xiayifan");
	writer.WritePropertyName("age");
	writer.Write (18);
	 writer.WritePropertyName("sex");
	writer.Write("男");
	writer.WriteObjectEnd ();

	Debug.Log(writer.ToString());

	------------输出结果----------
   {"name":"xiayifan","age":18,"sex":"男"}
```
2) 数组类型json

```c#
JsonWriter writer = new JsonWriter();
        writer.WriteArrayStart();
        writer.Write("one");
        writer.Write("two");
        writer.Write("three");
        writer.Write("four");
        writer.WriteArrayEnd();

        Debug.Log(writer.ToString());

        ------------输出结果----------
        ["one","two","three","four"]
```

## 2.解析JSON

(1) 使用JsonMapper解析上述JSON
```c#
JsonData jsonData2 = JsonMapper.ToObject(json2);
    Debug.Log(jsonData2["name"] + "  " + data2["info"]["sex"]);

    ---------------运行结果-----------------
    zhansan male
```

(2)使用JsonMapper解析JSON数据给指定对象

```c#
string json='{"name":"zhansan","age":28,"sex":"male"}';
   Player player=JsonMapper.ToObject<Player>(json);
   Debug.Log("name="+player.name+" age="+player.age);

   name=zhansan age=28
```

(3)遍历JsonData的key和value
由于JsonData实现了IDictionary接口，所以可以使用Foreach进行遍历
```c#
JsonData jd = new JsonData();
jd["name"] = "张三";
jd["age"] = 35;
IDictionary dic=jd as IDictionary;
foreach (string key in dic.Keys)
{
	print(key);
}
```
### 将对象和对象内容以键值对的形式进行保存

```c#
static void jsonTest3()
        {
            Person p1 = new Person();
            p1.name = "zhangsan";
            p1.age = 23;
            //将对象序列化为字符串
            JsonData userData = JsonMapper.ToObject(JsonMapper.ToJson(p1));
            JsonData jd = new JsonData();
            jd["user1"] = new JsonData();
            jd["user1"].Add(userData);//以数组的格式保存数据

            jd["user2"] = new JsonData();
            jd["user2"] = userData;//以对象的格式保存数据
            string jsonData = JsonMapper.ToJson(jd);
            Console.WriteLine("json=" + jsonData);

            //把json数据反序列化为对象
            JsonData json = JsonMapper.ToObject(jsonData);
            Person p = JsonMapper.ToObject<Person>(json["user2"].ToJson());
            Console.WriteLine("name=" + p.name + "  age=" + p.age);

            Person pp = JsonMapper.ToObject<Person>(json["user1"][0].ToJson());
            Console.WriteLine("name=" + pp.name + "  age=" + pp.age);

        }
```

运行结果：user1以数组的形式保存，user2以对象的形式保存 
json={“user1”:[{“name”:”zhangsan”,”age”:23,”adress”:null}], 
“user2”:{“name”:”zhangsan”,”age”:23,”adress”:null}} 
name=zhangsan age=23 
name=zhangsan age=23

### 将集合数据进行序列化和反序列化
```c#
public static void jsonTest4()
        {
            Person p1 = new Person();
            p1.name = "zhangsan";
            p1.age = 23;
            Adress adress1 = new Adress();
            adress1.province = "HeNan";
            adress1.city = "LuoYang";
            p1.adress = adress1;

            Person p2 = new Person();
            p2.name = "lisi";
            p2.age = 20;
            Adress adress2 = new Adress();
            adress2.province = "HeBei";
            adress2.city = "HanDan";
            p2.adress = adress2;

            List<Person> list = new List<Person>();
            list.Add(p1);
            list.Add(p2);

            //生成json数据
            string listJson = JsonMapper.ToJson(list);
            Console.WriteLine(listJson);
            Console.WriteLine("------------------------");
            //解析json
            List<Person> personJsonList = JsonMapper.ToObject<List<Person>>(listJson);
            for (int i = 0; i < personJsonList.Count; i++)
            {
                Console.WriteLine("name" + personJsonList[i].name);
            }

        }
```
运行结果 
[{“name”:”zhangsan”,”age”:23,”adress”:{“province”:”HeNan”,”city”:”LuoYang”}}, 
{“name”:”lisi”,”age”:20,”adress”:{“province”:”HeBei”,”city”:”HanDan”}}]














