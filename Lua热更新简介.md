# Uniyt3D-Lua

## 什么是热更新？
通常游戏上线后，玩家下载第一个版本（70M-200M左右或者更大），在运营的过程中，如果需要更换UI的显示，或者修改游戏的逻辑和资源的时。这个时候，如果不使用热更新，就需要重新打包，然后让玩家重新下载（浪费流量和时间，体验不好）。
热更新可以在不重新下载客户端的情况下，更新游戏的内容。
热更新一般应用在手机网游上。

## 关于热更新
### 为什么C#脚本不可以直接更新

C#是一门编程语言，它在运行之前需要进行编译，而这个编译的过程在移动平台无法完成，所以当我们游戏的逻辑更改，C#代码发生改变的时候，我们就需要重新在开发环境下编译，然后重新打包，然后让玩家去下载更新最新的版本，所以直接用C#语言的话不太适合。
这个体验差：包下载需要的时间长，而且很多资源没有更新，也需要重新下载，浪费流量。

### 热更新有哪些实现方式?

* 1.使用Lua脚本编写游戏的UI或者其他的逻辑。
* 2.使用C#Light
* 3.使用C#反射技术
* 4.Unity中的AssetBundle

## 关于AssetBundle

### 什么是AssetBundle?

Unity提供了一个资源热更新技术，就是通过AssetBundle,我们可以通过AssetBundle更新游戏UI，也可以把脚本或者其他代码当成资源打包成AssetBundle然后更新到客户端。
在所有的热更新技术中都需要AssetBundle

## Lua的解析技术有哪些?
在移动端可以编写Lua的解析器，通过这个解析器，可以运行最新的Lua脚本，然后我们把控制游戏逻辑的代码都协程Lua脚本。

## 不同版本Lua介绍
* luainterface

luainterface：LuaInterface是开源的C#的lua桥接库，配合开源库luanet，能轻松实现Lua，C#相互调用和参数事件传递。但作者仅完成了windows程序的功能实现，跨平台并没有完成，作者于2013年4月30日停止更新luainterface，并推荐大家关注luainterface的一个分支Nlua。Nlua是实现跨平台的Luainterface的升级版，uLua和NLua都是基于此库升级编写
  
* nlua

nlua：是LuaInterface的一个分支，继承了Luainterface的所有优点，并将Luanet库功能集成到代码中，实现跨平台（Windows, Linux, Mac, iOS , Android, Windows Phone 7 and 8），对ios平台做了特殊处理，如支持了委托的桥接。
配合NLua有2种Lua实现，第一种是KeraLua，基于原生Lua，将C API 进行简单的包装，使C# 可以方便使用 Lua C API，第二种是KopiLua，C#实现的Lua vm（对，和UniLua一样也是纯C#实现的Lua vm）。以下为关于两种方案的比较。
使用KeraLua，必须将lua 编译成 Unity3D Plugin，并将编译好的文件放到Plugins文件夹下相应的平台文件夹中。并定义#define USE_KERALUA
使用KopiLua，定义#define USE_KERALUA即可

* ulua
  
ulua：基于luainterface升级版，uLua = Lua + LuaJIT + LuaInterface，全平台支持。在原生C的基础上使用LuaJit进行加速，如果uLua效率高，LuaJit有很大功劳，作者仅仅提供了uLua插件包，并未提供整套插件源码。此外，作者重写了loadfile、print等api，使用非常简单，导入package，就可以开始编写代码了。
  
* unilua

unilua：是云风团队阿南的作品，是lua5.2的C#版，
纯C#的Lua 5.2实现，是不是感觉似曾相识，对的，KopiLua也是纯C#实现的Lua vm，虽然Unilua出名，但是没有KopiLua的配套库好用，其自身同的Ffi库，是实验性质的库，不完善，作者不推荐使用，虽然作者在其商业项目中使用，但是这只是其中一部分代码，Unilua和C#中间层的代码作者并没有开源。UniLua仅仅提供了Lua原生的接口，如果要在Lua代码中调用C#，使用就需要把Luanet 移植到Unilua代码中，总的来说很蛋疼，据推测Unilua方法都是使用Lua标准的命名方式，所以将luanet源码中所有C接口全部手动改写成Unilua 的接口，就可以使用，这个工作量，等闲的时候把玩比较好。

* cstolua

cstolua:cstolua是作者对ulua的扩展，提高了效率
 
* slua

slua：也是从ulua扩展而来，官方说效率比cstolua还高，不过也有很多人质疑过 http://www.ulua.org/cstolua.html http://www.slua.net/ http://www.sineysoft.com/post/164









