# Uniyt3D-

## ULua 框架内容介绍
* ULua 插件网址：http://ulua.org/download.html

* SimpleFramework + tolua #：http://doc.ulua.org/default.asp?cateID=4

* LuaFramework
LuaFramework是基于SimpleFramework + tolua #基础上，重新构造的新框架
https://github.com/jarjin/LuaFramework_UGUI (GitHub上下载源码)

* ServerFramework
基于lua热更新框架的服务器框架
https://github.com/jarjin/ServerFramework
### uLua框架下的文件夹的内容

__Examples__ ：框架自带的Demo例子，如果只需要框架的同学，里面的资源可以删除掉。去“疑难解答”里面查看方法。
—Builds：里面都是一些NGUI/UGUI定义的图集啊、Prefab等资源。用于生成assetbundle而准备的资源。
—Editor：里面是例子用到的一个新手引导步骤演示的编辑器脚本。
—Editor Default Resource：目录是新手引导步骤对话框用的的图片资源。
—Rsources：例子里面用于演示的一个内建的GUI容器的Prefab。
—Textures：里面是Buidls目录里面图集的原图文件。

__Scenes__：里面一个login场景文件也是cstolua自带的性能测试场景文件。

__Lua__：框架自带的Lua源码目录，用户自定义的Lua脚本也就是放在这里面，最后打包的时候，打包脚本会将其按目录结构生成到StreaminAssets目录里面去，然后在将其上传到游戏的Web服务器上面，用于准备被每个游戏客户端下载更新他们本地的Lua脚本。达到热更目的。
—3rd：里面是第三方的一些插件lua、实例源码文件，比如：cjson、pbc、pblua、sproto等。
—Common：公用的lua文件目录，如define.lua文件，一些变量声明，全局配置等，functions.lua常用函数库，通讯的protocal.lua协议文件。
—Controller：控制器目录，它不依赖于某一个Lua面板，它是独立存活在Luavm中的一个操作类，操作数据、控制面板显示而已。
—Logic：目录里面存放的是一些管理器类，比如GameManager游戏管理器、NetworkManager网络管理器，如果你有新的管理器可以放到里面。
—View：这是面板的视图层，里面都是一些被Unity调用的面板的变量，走的是Unity GameObject的生命周期的事件调用。

__Plugins__：ulua底层库所在的目录，里面存放的是不同平台的底层库，之所以ulua效率高，就是它是纯c的lua虚拟机，而不是c#解释型的。
—Andriod：安卓lua虚拟机底层库，里面分为armv7-a与Intel x86平台。
—iOS：里面就是苹果lua虚拟机底层库。
—ulua.bundle：里面是Mac机器的底层库。
—x86：里面是Win32/Linux32位机器的lua虚拟机底层库。
—x86_64：里面是Win64/Linux64位机器的lua虚拟机底层库。

__Scripts__：框架的C#脚本层，之所以这个目录跟lua目录都放在最外层，为了让用户一眼都能找到，明白是什么。
—Common：框架的公用定义类。LuaLoader（跟lua加载有关的类）、与luavm通知unity游戏对象的“LuaBehaviour”桥类。
—ConstDefine：常量定义目录，AppConst（应用常量）ManagerName（管理器名称）NotiConst（通知常量，用于mvc消息通知）。
—Controller：控制器目录，分为StartUpCommand启动控制器，跟常用逻辑控制器。框架接收到启动命令后，直接在启动命令里面注册所有的管理器类。
—Framework：经过修改过的PureMVC的框架文件。
—Manager：Unity提供基础功能的管理器类，音乐、面板、线程、资源等众多管理器。
—Network：网络的常用辅助类，ByteBuffer字节操作封装类，网络协议类，转换器类。
—Utility：常用工具类。
—View：C#用的PureMVC的视图层。

__ToLua__ (低版本的可能是uLua)：ulua/cstolua的核心目录，里面还有经过我们修缮后ulua的基础使用例子，用户初学者最佳。
—Core：顾名思义，ulua的核心目录，所有c#与lua的交互都是通过它进行调度的。
—Editor：这是供cstolua去反射定义Wrap文件列表的工具类目录。
—Examples：经过我们修改增加后ulua自带的例子。
—Source：这个是cstolua的核心目录，里面有Base核心目录，与动态生成用于存放LuaWrap类的缓存目录。

原来版本的消息结构为PureMVC，而新版的改成了：
AppFacade + Controller层通讯（修改版）+重写的View层通讯 = 0.3.8的框架

## 热更新UI生成步骤简介

### 第一步：生成wrap文件
Wrap,含义包裹,在程序中有封装的意思，使用wrap相当于对一个C#文件生成了一个包裹层，让其可以在lua中调用。
* 清空wrap
在编辑器中使用 Lua –>Clear wrap files 清空了ULuaFrameWork\Cilent\Assets\LuaFramework\ToLua\Source\ 下面的wrap文件
* 生成wrap
在编辑器中使用 Lua –>Gen Lua Wrap files 生成了c#的lua文件

### 第二步：搭建UI
一定要在项目中添加一个空物体，然后挂一个Global Generator组件，控制项目的开始
将创建的UI界面命名+Panel
将搭建好的UI界面做成一个预设体放到Prefabs文件夹中，然后创建预设体的AssetBundle名字（和其他模型的名字后缀要一样）
还要将UI用到的图片和字体等添加AssetBundel，使用的图片可以根据需要做成分组

### 第三步：修改Lua代码

#### 1.GameManager.lua
将框架中的GameManager改掉，或者自己写一个
```lua
require "Common/define"

require "Controller/BottomCtrl"
require "Controller/SettingsCtrl"

GameManager = {}
local this = GameManager

function GameManager.LuaScriptPanel() 
	return 'Bottom','Settings'
end

function GameManager.OnInitOK()
	  AppConst.SocketPort = 2012;
    AppConst.SocketAddress = "192.168.2.118";
    NetManager:SendConnect();

	  BottomCtrl.Awake()    --初始化BottomCtrl
	  SettingsCtrl.Awake()

end
```
#### 2.为每一个预设体写一个Panel.lua脚本

![](http://i4.bvimg.com/1949/7d481a1e928f9612.png)

##### BottomPanel

```lua
BottomPanel = {}

local this = BottomPanel

local gameObject
local transform

function BottomPanel.Awake(obj)
	gameObject = obj
	transform = gameObject.transform
	this.InitPanel()
end

function BottomPanel.InitPanel()

	this.buttonSettings = transform:FindChild("ButtonSettings").gameObject   --查找到Bottom中的三个按钮
	this.buttonPeople = transform:FindChild("ButtonPeople").gameObject
	this.buttonDialog = transform:FindChild("ButtonDialog").gameObject

end
```
##### SettingsPanel

```lua
SettingsPanel = {}
local this = SettingsPanel
local gameObject
local transform
function SettingsPanel.Awake(obj)
	gameObject = obj
	transform = gameObject.transform

	this.InitPanel()     --调用自身的InitPanel函数
end

function SettingsPanel.InitPanel()

	this.anim = transform:FindChild("BG"): GetComponent("Animator")    --获取对象身上的组件
	this.buttonClose = transform:FindChild("BG/ButtonClose").gameObject   

end
```

#### 3.对应Panel脚本写运行Ctrl脚本

##### BottomCtrl

```lua
require "Common/define"

BottomCtrl ={}
local this = BottomCtrl
local gameObject
local transform
local lua

function BottomCtrl.New()
  return this;
end

function BottomCtrl.Awake()
	PanelManager:CreatePanel('Bottom', this.OnCreate);
end

function BottomCtrl.OnCreate(obj)
	gameObject = obj;
	transform = gameObject.transform

	lua = gameObject:GetComponent('LuaBehaviour');    

	lua:AddClick(BottomPanel.buttonSettings, this.OnButtonSettingsClick);   --将Panel脚本中获取的对象注册按钮方法
	lua:AddClick(BottomPanel.buttonPeople, this.OnButtonPeopleClick);
	lua:AddClick(BottomPanel.buttonDialog, this.OnButtonDialogClick);

end
function BottomCtrl.OnButtonSettingsClick()

	SettingsCtrl.Show()
end
function BottomCtrl.OnButtonPeopleClick()

end
function BottomCtrl.OnButtonDialogClick()

end
```

##### SettingsCtrl

```lua
require "Common/define"


SettingsCtrl ={}

local this = SettingsCtrl

local gameObject
local transform
local lua
function SettingsCtrl.New()

	return this;
end


function SettingsCtrl.Awake()

	PanelManager:CreatePanel('Settings', this.OnCreate);
end


function SettingsCtrl.OnCreate(obj)
	gameObject = obj;
	transform = obj.transform
	lua = gameObject:GetComponent('LuaBehaviour');

	lua:AddClick(SettingsPanel.buttonClose, this.OnBtnClick);
end

function SettingsCtrl.OnBtnClick()
	this.Hide()
end
--SettingsPanel界面的显示与隐藏
function SettingsCtrl.Show()
	SettingsPanel.anim:SetBool("IsSHOW",true)
end
function SettingsCtrl.Hide()
	SettingsPanel.anim:SetBool("IsSHOW",false)
end
```

### 第四步：配置服务器

找到下载的SipleFramework文件夹，点击Server文件夹，启动Server项目，找到HttpServer脚本，然后将里面的IP地址改为要连接的服务器IP，一定要重新生成项目，确定更改了内容

在unity中找到AppConst脚本，如果是在Unity中运行的话， DebugMode = true; 如果是要运行到手机中要改为False，还要将IP改为连接的IP和端口UpdateMode（更新模式）发布的时候可以改为true

将这些做完之后可以将在Unity菜单栏中的Game中选择将AssetBund上传到服务器中，如果是在Windows中测试，选择Build AssetBund Windows，

### 第五步：发布安卓

将运行平台更改为安卓平台之后，按第一步重新生成wrap文件，AppConst脚本的DebugMode = false
将这些做完之后可以将在Unity菜单栏中的Game中选择将AssetBund上传到服务器中，因为要在安卓手机运行，选择Build AssetBund Android，重新生成一次

### 第六步：

更新UI界面内容时，只需要将预设体中的内容改变，然后将Lua脚本中的内容更改就可以，也可以新创建一个UI界面，重新添加Panel和Ctrl脚本，添加到GameManager中

然后重新Build一下就可以在手机那边进行更新加载了



























