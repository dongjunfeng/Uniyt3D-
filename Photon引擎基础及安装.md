# Uniyt3D-Photon

## Photon介绍

### 什么是Photon
Photon 是一个泛用性的ScoketServer套装软件，可用于多人在线游戏、聊天室、大厅游戏，并同时
支持Windows、Unity3D、iOS、Android、Flash等平台。

以前做网络游戏都要花费大量的金钱及人力开发游戏引擎（Game Enngine）及服务器（Game Server）,但随着技术的进步及游戏开发成本越来越高，开始有了成型的游戏引擎，像Unity3D、UDK等等，当引擎有了成型的,服务器当然也会出现成型的，像比较常用切价格便宜的服务器引擎如：SmartFox Server、Electro Server、Photon Server等，当然还有收费相对较高的服务器如：BigWorld Server，这些成型的游戏服务器为游戏公司省下大量的开发费用，也让一些小型公司或独立制作团队有了开发网络游戏的能力，尤其在社群游戏盛行的这个年代这些成型的服务器便大受欢迎。

Photon 内建一套大厅游戏服务及MMO游戏服务器，都含有源代码，使用者可以拿来修改成自己所需要或直接继承后加入自己的游戏逻辑中。

### Photon SDK 简介
简单的说,Photon就是用c# 来做服务器的最佳入口

Photon的组织架构图

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/PhotoServer.png)

包含下面几个特点:
1. 实时的,基于回合制的,或者MMO类型的
2. 多人处理的框架结构
3. 跨平台的部署
4. 很高的扩展性
5. 可定制化编程

### 平价服务器比较

市面上有几个价格较为便宜的游戏服务器，下图列出的是比较受欢迎的几个，这几个服务器都有很好的效果与架构，本课程主要是以Photon为主，其他服务器有机会建议接触一下，都有免费版本可以使用。其实不管是游戏引擎还是服务器它们都是开发工具，没必要局限于某一个上，尽量去增大自己的视野以及自己创作空间。

市面上主要的Server比较表格

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/Image.png)

以上是几个游戏服务器都有提供商用的免费版本,可以拿来作为商业用途,只要在前面显示Server的Logo即可.

### 使用Photon的理由

1.Photon的核心C++,性能上要优于平价服务器.

2.因为Photon Server的SDK使用的是C#开发，因此使用资料库比Java架构的SFS货ES5好不少，不用屈就低效能的ODBC或开发门槛高的Corba.

3 Photon有提供Win32 C++跟Mac 的客户端（Client）,可选用更多的游戏，经过适当的组件包装，连不支持的平台都可以使用.

4 2011年3月Photon与Unity合作提供一个MMO解决方案,Unity是广受独立开发者欢迎的引擎，可于Photon得到最佳的搭配。

5.Photon 本身也在不断的发展,包括将来出现的Photon Clound.

### 使用Photon的问题点

1.Photon Server 以前只能架在Windows上,官方已提出会出Linux版本.

2.缺少中文的文件教学，更多Photon特殊及问题直接使用Photon官网
http://www.exitgames.com/

## 安装Photon

### 1.注册会员
登录官网 http://www.exitgames.com/ 注册会员 注册会员是免费的,所以最好先注册一个会员.（本人账户365757560@qq.com，密码djf123456）

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/PhotoServer01.png)

### 2.下载

在官网 http://www.exitgames.com/ 下载Photon,，Client SDK可选择性下载，直接下载Server SDK会内置.Net及Unity的Client DK，不过另外下载的Client SDK会比较新一点。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/PhotoServer03.png)


Licenses 可无限制任务30天或者100人免费，这个可以点击用户头像，选择[Your Server]找到[Free License](/resource/k25/03_引擎高级进阶/项目发布/Photon基础/100 CCU,no expiry)],下载到直接的硬盘中.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/PhotoServer04.png)

### 3.解压

将Server SDK解压到自己的硬盘，不需要安装，来解压即可使用，装到主机上后可将Photon设为Windows服务.（可以解压到C盘之外的硬盘，创建一个文件夹解压）

### 4.安装授权

找到解压的目录底下的[deploy]目录bin_Win32(32位)或者bin_Win64(64位).

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/Image2.png)

进入文件夹后，请将之前下载的License用户授权文件放到这个文件夹内

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/Image3.png)

之后只要启动Server,Photon Server 便会自己放到文件夹底下的授权文档.

### 5.启动Server

执行在目录bin_Win32(32位)或者bin_Win64(64位)的[PhotonControl.exe],在工作列上会出现Photon的icon.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/Image4.png)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/Image5.png)

接下来在Photon icon 上按右键点击Load Balancing执行[Photon>Start as application]之后再执行[Open Logs]
等到Log画面出现[Service is running…]就是启动完成了.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E5%9F%BA%E7%A1%80/images/Image7.png)

## Phonton目录认识

解压出来是四个文件
* deploy 主要存放photon的服务器控制程序和服务端Demo，（注：此文件夹是重要的文件夹哦，photon server 的运行文件在次文件夹中）。打开文件夹，分别有bin_Win32和bin_Win64文件夹对应不同操作系统，打开两个文件夹后PhotonControl.exe便是photonServer的启动文件。
* doc 文档
* lib Photon类库
* src-server 服务端Demo源代码
* build：编译的文件

## 服务器端

启动Visual Studio 新建项目(server)(创建一个C#类库)，添加两个项目文件名字为：ChatPeer和CharServer ，并配置PhotonServer.config文件

* 1.添加引用：右键引用，点击添加引用，选择浏览，在第1步的lib文件夹中先责标红的三个dll文件(ExitGamesLibs.dll,Photon.SocketServer.dll,PhotonHostRuntimeInterfaces.dll)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E9%A1%B9%E7%9B%AE%E5%8F%91%E5%B8%83/Photon%E9%85%8D%E7%BD%AE/images/20170316121328872.png)

* 2.右键项目，选择属性，出现下图所示，选择输出路径。在第一步解压的deploy文件夹中新建一个ChatServer文件夹，再在其中创建一个bin文件夹，点击浏览选择此文件夹。完毕后，生成项目(点击启动)。

![](http://img.blog.csdn.net/20170316121935427?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSmFzb25NYTE5OTE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

* 3.在deploy文件中有一个PhotonServer.config文件，用编辑软件打开（visual studio亦可），进行编辑。

 1. 在LoadBalancing (MyCloud)内部找到一个TCPListener标签项，复制一个，然后定义端口号和OverrideApplication = 服务端项目名称的名字。这是使用TCP方式通讯的配置（端口号是测试后定义的，读者可根据配置文件和需求自己定义），

![](http://img.blog.csdn.net/20170316123537809?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSmFzb25NYTE5OTE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

 2.在Applications内部添加一个Application标签项，修改：
 配置PhotonServer.config文件如下:
* Name:项目名字
* BaseDirectory:根目录，deploy文件夹下为基础目录
* Assembly ：是在生成的类库中的bin目录下与我们项目名称相同的.dll文件的名字
* Type:是主类的全称，在这里是：MyServer.MyApplication，一定要包括命名空间
* EnableAutoRestart：是否是自动启动，表示当我们替换服务器文件时候，不用停止服务器，替换后photon会自动加载文件

![](http://img.blog.csdn.net/20170316123541716?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSmFzb25NYTE5OTE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)


## Unity客户端

新建一个plugin文件夹，把第一步解压的lib文件中的Photon3Unity3D.dll文件拖拽到plugin文件夹中
把在MainCamera上添加一个C#脚本PhotonServerEngine。

以上准备工作做好后，可以写程序了

1、在Unity客户端创建的脚本里面
```c#
using UnityEngine;
using System.Collections;
using ExitGames.Client.Photon;
using System.Collections.Generic;

public class TextPhoton : MonoBehaviour,IPhotonPeerListener {
    PhotonPeer mypeer;
    private bool isConnected = false;
	// Use this for initialization
	void Start () {
        //与服务器建立连接（TCP协议）
        mypeer = new PhotonPeer(this, ConnectionProtocol.Tcp);
        mypeer.Connect("192.168.2.118:4532", "ChatServer");  //连接时提供IP和端口

	}
	
	// Update is called once per frame
	void Update () {
        mypeer.Service();   //发送请求
	}
    private void OnGUI()
    {
        if (isConnected)
        {
            if (GUILayout.Button("Send a opertion."))
            {
                Dictionary<byte, object> dict = new Dictionary<byte, object>();
                dict.Add(1, "text");
                dict.Add(2, "1234");
                mypeer.OpCustom(1, dict, true);   //向服务器发起请求(1代表发送消息类型）
                
            }
        }
    }
    //打印服务端返回的等级和消息
    public void DebugReturn(DebugLevel level, string message)
    {
        
    }
    //调用执行的事件
    public void OnEvent(EventData eventData)
    {
        
    }
    //用来处理服务端返回的消息
    public void OnOperationResponse(OperationResponse operationResponse)
    {
        print("得到服务器向客户端的回应！");
        Dictionary<byte, object> newParam = operationResponse.Parameters;
        foreach (var parm in newParam.Values)
        {
            print(parm);
        }
        print(operationResponse.DebugMessage);
    }
    //检测连接状态
    public void OnStatusChanged(StatusCode statusCode)
    {
        switch(statusCode)
        {
            case StatusCode.Connect:
                print("我已经连接Photon服务器");
                isConnected = true;
                break;
            case StatusCode.Disconnect:
                print("断开服务器");
                break;
        }
    }
}
```
## 服务端创建的项目的脚本

### ChatPeer.cs
```
using Photon.SocketServer;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace server
{
    //用来和客户端通信的
    class ChatPeer :ClientPeer
    {
        public ChatPeer(InitRequest initRequest) : base(initRequest)
        {

        }
        //当断开连接调用
        protected override void OnDisconnect(PhotonHostRuntimeInterfaces.DisconnectReason reasonCode, string reasonDetail)
        {
            
        }
        //服务端处理客户端消息，当客户端发起请求时调用
        //                                           接收客户端传送过来的请求
        protected override void OnOperationRequest(OperationRequest operationRequest, SendParameters sendParameters)
        {
            switch(operationRequest.OperationCode)  //判断客户端发送请求的类型
            {
                case 1:
                    if (operationRequest.Parameters.Count < 2)          //若传过来的参数小于2
                    {
                        OperationResponse operationResponse = new OperationResponse(operationRequest.OperationCode);
                        operationResponse.DebugMessage = "登录失败";
                        operationResponse.ReturnCode = 2;
                        SendOperationResponse(operationResponse, sendParameters);  //向客户端发送回应
                    }
                    else
                    {
                        string userID = (string)operationRequest.Parameters[1];
                        string userPW = (string)operationRequest.Parameters[2];
                        //与服务端传送的数据进行判断
                        if(userID == "text" && userPW == "1234")     //账号密码相同的情况
                        {
                            Dictionary<byte, object> paramters = new Dictionary<byte, object>();
                            paramters.Add(1, userID);
                            paramters.Add(2, userPW);
                            OperationResponse operationResponse = new OperationResponse(operationRequest.OperationCode,paramters);
                            operationResponse.DebugMessage = "登录成功";
                            operationResponse.ReturnCode = 1;
                            SendOperationResponse(operationResponse, sendParameters);
                        }
                        else
                        {
                            OperationResponse operationResponse = new OperationResponse(operationRequest.OperationCode);
                            operationResponse.DebugMessage = "账号密码错误！";
                            operationResponse.ReturnCode = 0;
                            SendOperationResponse(operationResponse, sendParameters); 
                        }
                    }
                    break;
            }
        }
    }
}
```

### ChatServer.cs

```c#

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Photon.SocketServer;

namespace server
{
    //Photon服务器部署的时候回调用
    public class ChatServer :ApplicationBase
    {
        //当一个客户端连接到这个服务端的时候调用
        protected override PeerBase CreatePeer(InitRequest initRequest)
        {
            return new ChatPeer(initRequest);   //连接成功后，返回一个ChatPeer,负责与客户端进行通信
        }
        //当这个server端启动的时候调用
        protected override void Setup()
        {
           
        }
        //当这个server端被停掉的时候调用
        protected override void TearDown()
        {
            
        }
    }
}
```



