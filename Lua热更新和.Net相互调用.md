# Uniyt3D-热更新

## 什么是LuaInterface?
* LuaInterface包括两个核心库一个是LuaInterface.dll,一个是Luanet.dll，我们可以通过LuaInterface完成Lua和C#(CLR)之间的互相调用

## 在C#中执行访问Lua代码
* 想要在C#中调用Lua，需要引用LuaInterface插件
```c#
using LuaInterface;
static void Main(string[] args)
{
Lua lua = new Lua();	//创建Lua解析器
lua["num"]=2;	//定义一个num
lua["str"]="a string";	//定义一个字符串
lua.newTable("tab");	//创建一个表  tab={}
}

取得Lua环境中的变量：
double num = (double)lua["num"];
string str = (string)lua["str"];
```
## 在C#中执行Lua脚本文件,或者脚本字符串

### 在C#中执行Lua语句
```c#
lua.DoString("num=2");
lua.DoString("str='a string'");

lua.DoString("function testFunc() print(' lua test func')end    testFunc() ");  --  加上一段lua程序并执行
在热更新中，只需要写好解析lua脚本的代码，然后c#代码不需要变动，只需要修改lua脚本就好，通过lua脚本控制游戏逻辑。
```
### 在C#中执行Lua文件
```c#
注意：想要直接使用文件夹的名字调用，必须将lua文件放到项目中运行的目录，bin-->Debug中
lua.DoFile("script.lua");//执行script.lua脚本

--[lua]-- lua文件  
a = 0.5
c = 0.6

double c = (double)lua["c"]; -- 读完文件之后获取lua中的变量值
```
### lua和C#中类型的对应

```c#
Lua中             C#中
nil 		          null
string 		     System.String
number 	       System.Double
boolean 	     System.Boolean
table		      LuaInterface.LuaTable
function 	    LuaInterface.LuaFunction
```

### 把一个C#方法注册进Lua的一个全局方法

```c#
//把一个类中的普通方法注册进去
//                  要注册的方法名，对象，对象的方法类型
lua.RegisterFunction("NormalMethod",obj,obj.GetType().GetMethod("NormalMethod"))
public void NormalMethod()
{
		Console.WriteLine(" NormalMethod Suc !!");
}
lua.DoString(" NormalMethod()");
//把一个类的静态方法注册进去
//                  ：要注册的方法名，空，类名调用该静态函数
lua.RegisterFunction("StaticMethod",null,typeof(ClassName).GetMethod("StaticMethod"))
public void StaticMethod()
{
		Console.WriteLine(" StaticMethod Suc !!");
}
lua.DoString(" StaticMethod()")
```
## 在Lua中使用c#中的类

### 在Lua中使用c#中的类
```lua
--在Lua中调用C#需要将luanet插件与lua文件放到同一个文件夹
require "luanet"        
--加载CLR的类型、实例化CLR对象
luanet.load_assembly("System.Windows.Forms") --调用方法使用的using集
luanet.load_assembly("System.Drawing")          --调用方法所在的命名空间
Form = luanet.import_type("System.Windows.Forms.Form")    --调用方法所在的类
Deno = Form（）                   --创建该类的对象，通过对象调用该类里面的属性与方法
StartPosition = luanet.import_type("System.Windows.Forms.FormStartPosition")
print(Form)
print(StartPosition)
在Lua中使用C#中的类创建对象的时候，会自动匹配最合适的构造方法
```
### 在Lua中访问C#中的属性和方法

* Lua代码中，访问C#对象的属性的方式和访问table的键索引一样，比如obj.name 或者 obj[“name”]
* Lua代码中，访问C#对象的普通函数的方式和调用table的函数一样，比如obj:method1()    普通方法要用对象加：调用，静态方法要通过类名加.的方法调用

### 在Lua中访问C#中的方法-特殊情况  --ref和out
当函数中有out或ref参数时，out参数和ref参数和函数的返回值一起返回，并且调用的时候，out参数不需要传入
C#函数定义
```c#
class Obj{
int OutMethod(int parameter1,out parameter2){
	  parameter2=34;
	  return parameter1;
  }
int RefMethod(int parameter1,ref parameter2){
	  parameter2=parameter2+2;
	  return parameter1+parameter2;
  }
 }
 ```
在lua文件中调用该方法
```lua
num,mun1 = obj:OutMethod1(34)    --因为有out返回值和return返回，所以需要用两个变量接收，只能有一个out参数，不然return返回的数会被最后一个out的数给覆盖
 --out参数不需要参数，这个返回一个table，里面的值为parameter1,parameter2
(34,34)

value1,value2 = obj:OutMethod2(10,10)  --ref需要传入参数，并且需要返回值接收，如果超过一个ref参数，返回值的值会被最后一个ref参数的值覆盖
--ref参数需要传入，返回一个table有两个值(value1,value2)
```
### 在Lua中访问C#中的方法-特殊情况 --重载方法的调用

当有重载函数的时候，调用函数会自动匹配第一个能匹配的函数
可以使用 __get_method_bysig__ 函数得到C#中指定类的指定参数的函数用法

```c#
[lua]
luaMethod = luanet.get_method_bysig(obj,"method","System.String") --调用字符串参数的重载函数
luaMethod("fsaettt")

luaMethod = luanet.get_method_bysig(obj,"method","System.Int32")   --调用int类型参数的重载函数
luaMethod(1)
[cs]
public void method(string str)
{
		System.Console.WriteLine(" Obj method string 111 ");
}

public void method(int str)
{
		System.Console.WriteLine(" Obj method int 打印出来的值 " + str);
}
```










