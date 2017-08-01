# Uniyt3D-Lua

## Lua语言简介

### Lua是什么？

Lua 是一个小巧的脚本语言。是巴西里约热内卢天主教大学（Pontifical Catholic University of Rio de Janeiro）里的一个研究小组，由Roberto Ierusalimschy、Waldemar Celes 和 Luiz Henrique de Figueiredo所组成并于1993年开发。 其设计目的是为了嵌入应用程序中，从而为应用程序提供灵活的扩展和定制功能。Lua由标准C编写而成，几乎在所有操作系统和平台上都可以编译，运行。Lua并没有提供强大的库，这是由它的定位决定的。所以Lua不适合作为开发独立应用程序的语言。Lua 有一个同时进行的JIT项目，提供在特定平台上的即时编译功能。

### Lua的编辑工具安装和下载

* 1,Lua的官网 lua.org
* 2,Luaforwindows

   http://luaforge.net/projects/luaforwindows/
   
   http://luaforwindows.luaforge.net/ (可安装的exe文件,一整套的Lua开发环境，有Lua的解释器，参考手册，范例和库，文档，和编辑器)
* 3,LuaStudio

  LuaStudio 是一款轻量级的优秀的可调试的Lua IDE,非常方便的用于lua代码的编写和调试.
  
## 编写第一个Lua程序
 
### Hello World
* 1，找到luaforwindows的安装目录，找到SciTE
* 2，打开SciTE，写入第一行Lua代码
```
  print(“Hello World”)
```
```
  local a = 1
  local b = 2
  打印多个元素的内容 print(a,b)
```
* 3，保存代码，保存为HelloWorld.lua
* 4，运行代码

## lua中的关键字

下面列出了一些在Lua中的保留字。这些保留的字不可以被用作常量或变量，或任何其它标识符。
Lua的保留字如下：关键字不能当做标示符。Lua大小写敏感。

and break do else
elseif end false for
function if in local
nil not or repeat
return then true until
while

## 注意事项
* 1,print()是Lua内置的方法
* 2,在Lua中字符串用""或者’’都可以表示
* 3,Lua中每一条语句后面是没有；号的
* 4,单行注释 -- 注释内容 --
* 5,多行注释 --[[ 这里是注释内容 ]]--

## 如何定义变量

### Lua中定义变量

lua是一个弱类型语言,不具有强类型语言的特点,比如
num = 100
这里定义了一个全局变量叫做num,赋值为100
在Lua中定义变量是没有类型的，根据存储什么数据，来决定是什么类型
变量的命名不能以数字开头
尽量避免下划线加大写字母开头，这种格式Lua自身保留
推荐使用C#中的命名规范和驼峰命名

## Lua中5种变量类型

### Lua中变量如下：
* 1，nil表示空数据，等同于null
* 2，boolean 布尔类型，存储true和false
* 3，string 字符串类型，字符串可以用双引号也可以使用单引号表示
* 4，number小数类型（Lua中没有整数类型）
* 5，table表类型

  myTable = {34,34,2,342,4}
  
  myTable[3]
  
我们可以使用type()来取得一个变量的类型
```Lua
  m =3
  print(type(m))  --打印number

  o = "32rer"
  print(type(o))  --打印string

  n =nil
  print(type(n))  --打印nil
```

## 局部变量和全局变量

### 局部变量和全局变量注意事项

默认定义的变量都是全局的，定义局部变量需要在前面加一个local；
在代码块中声明的局部变量，只会在当前作用域之类起作用,在lua中重复定义不会报错.
```
* temp = 34 – 全局
* local temp = 345 – 局部
```
```Lua
b = "global"
function myfunc()
	local b = "local variable"   --local表示局部变量
	a = "local variable"         --全局变量在函数里没有local关键字也表示全局变量
	print(a,b)                  --方法内会优先使用局部变量
end
myfunc()
print(a,b)                      --方法外使用全局变量
```
## Lua支持的运算符

### Lua中运算符有哪些：
* 1，算数运算符 + - * / % (Lua中没++ – 这样是运算符)

* 2，关系运算符 <= < > >= == ~=

* 3，逻辑运算符 and or not 分别表示 与 或 非（类似于C#中的 && || !）

a and b:当a为真时返回b,当a为假时,返回a   <=>   条件表达式 a?b:a

a or b:当a为真时返回a, 当a为假时返回b   <=>   条件表达式 a?a:b

not a:当a为真时返回假,当a为假时返回真   <=>   条件表达式 a?false:true
```lua
local a = false
    b = 5
    local c = a and b     --a为false，所以c = a
    print (tostring(c))     --打印false
```
## 流程控制 if语句

### if语句的三种用法：
* 1，if语句
```lua
if [condition] then  -- 一定是与then 对应起来使用
end
```
* 2，if else语句
```lua
if [condition] then
else
end
```
* 3，if elseif else语句
```lua
if [condition] then
elseif [condition]
else
end
```
* 4，if not 语句
```lua
if not false then
print(“ 如果不是”)
end
```
```lua
a = 2
if a == 1 then                       --if判断语句
	print("a is one")
else
	print("a isnot one")      --打印a isnot one
end
```
```lua
b = (a == 2) and "one" or "not one"
 上面的公式等价于

	if a == 2 then
		b = "one"
	else
		b = "not one"
	end
```

## 循环结构while循环
### 循环结构while循环:
* 1，while语法结构
```lua
while [condition] do
end
```
* 2，输出1到100
```lua
i = 0
while i < 100 do
	i = i + 1
	print(i)
end
```
3，实现1加到100
```lua
a = 0
b = 0
while a < 100 do
	a = a + 1;
	b = b + a;
end
print(b)    --打印5050
```
4，遍历1-100中所有的奇数的和
```lua
a = 0
b = 0
while a < 100 do
	a = a + 1;
	if a % 2 ~= 0 then   --判断a为奇数
		b = b + a;
	end
end
print(b)
```
## 循环结构repeat循环

### 循环结构repeat循环:
（有点类似与C#中的do..while循环）

* 1，语法结构
```lua
repeat
  [code to execute]
  until [condition]

  local a = 1
  repeat
  	a = a +1
  	print (tostring(a))  --打印2-11
  until( a>10 )
```
* 2，输出1到100
```lua
a = 0
 repeat
  	a = a +1
  	print (a)
  until( a ==100 )
```
* 3，实现1加到100
```lua
a = 0
b = 0
repeat
	a = a + 1
	b = b + a

until(a == 100)
print(b)    --打印5050
```

* 4，遍历1-100中所有的偶数的和
```lua
a = 0
b = 0
repeat
	a = a + 1
	if a % 2 == 0 then
		b = b + a
	end
until a == 100
print(b)    --打印2550
```
## for循环结构

### for循环结构：
* 1，语法结构
```lua
for index = [start],[end] do
[code to execute]
end
```
* 2，输出1到100
```lua
for a = 1,100 do
	print(a)
end
```

* 3，实现1加到100
```lua
b = 0
for a = 1,100 do
	b = b + a
	end
print(b)
```
* 4，遍历1-100中所有的奇数的和
```lua
b = 0

for a = 1,100,2 do   --a从1循环到100，步长为2
	b = b + a
	end
print(b)
```
* break可以终止循环 没有continue语法

## 函数（方法）

### Lua中定义函数：

* 1，如何定义函数

function 关键字表示函数开始,后接函数名和函数体 end表示函数结束

```lua
function [function name](param_1,param_2)
 [function code]
end
```
定义一个函数用来求得两个数字的和
```lua
function add(num1,num2)
    return num1+num2
 end

 local d = add(3,4)
 ```
 一个函数返回多个值
 ```lua
 function tear(a,b)
	return a+1,b+1
end

x,y = tear(1,2)
print(x,y)    --打印 2,3

x,y,z = tear(1,2)
print(x,y,z)    --打印 2,3，nil
```
```lua
function Demo(a,b,c)                     --function函数返回值return
	return a,b,c,"hello",3,false
end

q,w,e,r,t,y = Demo("dwed",3,true)
print(q,w,e,r,t,y)            --打印"dwed",3,true，"hello",3,false
```
定义一个函数，将第二个参数作为占位符加到第一个参数中
```lua
--将第二个参数给到第一个参数的代替值中

function printf(fmt,...)
	io.write(string.format(fmt,...))
end

printf("Hello %s from %s on %s\n",os.getenv"USER" or "there",_VERSION,os.date())   --打印Hello there from Lua 5.1 on 07/31/17 19:23:12

printf("hello %s \n","world")   --打印hello world 
```

## 标准库(标准函数)
### 内置标准函数

Lua内置提供了一些常用的函数帮助我们开发
* 1，数学处理的math相关函数
* 2，字符串处理的string相关函数
* 3，表处理的table相关函数
* 4，文件操作的io相关函数

### 文件操作
```lua
file = io.open("D:\\1.txt","w+")   --在D盘中创建一个1.txt的文本 “w+”为特殊字符
  file:write("32432","a")         --将两个字符串写入到文档中
  file:close()
```
### 数学运算函数
* math.abs(x) 返回x的绝对值。(整数/浮动)
* math.cos(x) 返回x的余弦值 (假定为弧度)
* math.max(x，…) 返回参数的最大值
* math.maxinteger(x) 一个整数的最大值为整数
* math.min(x,…) 返回参数的最小值
* math.sqrt (x) 返回x的平方根

等等。。

### 字符串处理相关函数
* string.len(s) 接受一个字符串,并返回它的长度。
* string.lower(s) 接收一个字符串并返回该字符串的副本与所有大写字母改为小写
* string.upper（s） 接收一个字符串并返回该字符串的副本与所有小写字母改为大写。
* string.format(s)
```
str = string.format("字符串：%s\n整数：%d\n小数：%f\n十六进制数：%X","qweqwe",1,0.13,348)   --将后面的参数添加到第一个字符串的占位符中
```
* string.match(s) 对目标字符串进行匹配，并找到匹配的字符段
```lua
print(string.match("hello lua", "lua"))    --找到两个字符串的相同的连续字符，并输出
print(string.match("data :2017/6/2", "%d+/%d+/%d+"))  --按照模式进行匹配
print(string.match("lua2 lua3", "lua%d", 2)) -- 匹配后面这个字符串
```
* ".." 字符串相加
* tostring() 把一个数字转化成字符串 如 local d = tostring(s)
* tonumber() 把一个字符串转化成数字 local s = tonumber(d)

  在lua中有默认的字符串和数字的自动转换:
  ```lua
  print("10"+1)  --  11  number类型 ，字符串类型和数类型直接想加就转换成数字类型
  local b = 10+"string" -- 错误  不能这样相加
  local b = "string"..10  --正确输出string10
  ```
### table表的赋值与创建

* table的赋值
```lua
myTable[3]=34  当键是一个数字的时候的赋值方式
myTable["name"]="newbieol" 当键是一个字符串的赋值方式
myTable.name = "shylock"当键是一个字符串的赋值方式
```

* table的访问
```lua
myTable[3]  --当键是数字的时候，只有这一种访问方式
myTable.name --当键是字符串的时候有两种访问方式
myTable["name"]
```

* table的第一种创建方式
```lua
myTable = {name="shylock",age=18,isMan = true}--	（表创建之后依然可以添加数据） 数据访问
myTable.name == "dong"  --可以更改表中的内容
myTable["name"]
```

* table的第二种方式(类似数组的使用)
```lua
 myTable = {34,34,34,3,4,"sdfdsf"}
```
__当没有键的时候，编译器会默认给每一个值，添加一个数字的键，该键从1开始__

### 表的遍历两种方式：

* 1,如果是只有数字键，并且是连续的可以使用下面的遍历

```lua
for index = 1,table.getn(myTable) do
	[code to execute]
end

local num = {1,3,43,43534,43,435,5} --默认是连续的
for index = 1,table.getn(num) do
	print ( tostring( num[index]) )    --打印1,3,43,43534,43,435,5
end

print ( "\n" )

local num = {[2]=1,[9]=3,43,43534,43,435,5} --非连续的
for index , value in pairs(num) do
	print ( index,value)    
--[[打印   遍历将索引为2的1被覆盖
1	  43
2	  43534
3	  43
4	  435
5	  5
9	  3            
]]--
end
print ( "\n" )
```

* 2，表中通过pairs 和 ipairs进行遍历:
```lua
for index,value in pairs(myNames) do
    print(index,value)
end
print ( "\n" )

local tt =    
{    
    [1] = "test3",    
    [9] = "test4",    
    name = "test5"    
}    

for i,v in ipairs(tt) do    -- 当index不连续的时候或不是数字值时，不能完全遍历table中的值
    print( tt[i] )           --只能打印"test3"
end  

for i,v in pairs(tt) do    --  当index不连续的时候，也可以完全遍历table中的值
    print( tt[i] )         --打印test3  test4  test5
end
```
### 表相关的函数

* 1.table.concat 把表中所有数据连成一个字符串
```lua
local string_concat = {"string", "int", "char", "float", "double"}  
local _tempStore_string = table.concat(string_concat,"-",3);  -- 最后一个参数表示开始的下标,也可以只写表名，可以将表中的内容组成一个字符串
print(_tempStore_string)      --打印结果char-float-double
```
* 2,table.insert 向指定位置插入一个数
```lua
local string_concat = {"string", "int", "char", "float", "double"}  
table.insert(string_concat,5,"3243");      --在索引为5的位置处插入一个“3243”
for index,value in pairs(string_concat) do
    print(index,value)
end
```
* 3,table.remove 移除指定位置的数据
```lua
local string_table = {"string", "int", "char", "float", "double"}  
table.remove(string_table,4);               --将索引为4的内容移除
for index,value in pairs(string_table) do
    print(index,value)
end
```
* 4,table.sort 排序
```lua
local string_table = {1,4,2,5,3}    
for index = 1,table.getn(string_table) do
	print ( tostring( string_table[index]) )
end
print ( "\n" )
table.sort(string_table);         --排序，将表默认从小到大排序，如果表内容都为字符串，将按照首字母先后排序，不能字符串和数字一起排序
table.sort(concat_table,function(v1,v2) return v1 > v2 end)  --将表从大到小排序

for index = 1,table.getn(string_table) do
	print ( tostring( string_table[index]) )
end
print ( "\n" )
```

### 通过表来实现面向对象

* 通过表来实现面向对象
```lua
Buff={life=100}  --申明Buff 表并定义life对象

function Buff.getBuff(self,a)
  self.life = self.life+a
end

function Buff:getBuff(a)
  self.life = self.life+a
end

Buff:getBuff(80) -- 冒号的调用方式
print(Buff.life)     --打印180

Buff.getBuff(Buff,80) -- 点号的调用方式
print(Buff.life)   --打印260，因为上面的程序已经将表中的life变成了180
```

### 通过常见的控制程序实现continue功能
```lua
for insert = 1,10 do
	while true do
		if insert == 5 then
			break
		end
		print(insert)
		break;
	end
end
--打印的结果跳过了5
```












