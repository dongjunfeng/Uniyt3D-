# Uniyt3D-Soket

## OSI网络7层模型

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image.png)
![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image1.png)

网络七层模型详解地址 ：http://www.2cto.com/net/201310/252965.html

## OSI网络七层模型与TCP/IP四层模型对比

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image2.png)

## 详细的TCP/IP网络模型

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image3.png)

## TCP/IP定义以及模型各层的概念

* TCP/IP（Transmission Control Protocol/Internet Protocol）即传输控制协议/网间协议，是一个工业标准的协议集，它是为广域网（WANs）设计的。

* UDP（User Data Protocol，用户数据报协议）是与TCP相对应的协议。它是属于TCP/IP协议族中的一种。

* 应用层 (Application)：应用层是个很广泛的概念，有一些基本相同的系统级 TCP/IP 应用以及应用协议，也有许多的企业商业应用和互联网应用。

* 传输层 (Transport)：传输层包括 UDP 和 TCP，UDP 几乎不对报文进行检查，而 TCP 提供传输保证。

* 网络层 (Network)：网络层协议由一系列协议组成，包括 ICMP、IGMP、RIP、OSPF、IP(v4,v6) 等。

* 链路层 (Link)：又称为物理数据网络接口层，负责报文传输。

## 网络交互

### 网络编程相关

互联网 通过 IP 定位电脑
在电脑中通过 Port 定位程序
程序和程序间 通过 协议定义通信数据格式

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image4.png)

## Socket相关概念

### IP地址
* 每台联网的电脑都有一个唯一的IP地址。
* 长度32位，分为四段，每段8位，用十进制数字表示，每段范围 0 ~ 255
* 特殊IP：127.0.0.1 用户本地网卡测试
* 版本：V4(32位) 和 V6(128位，分为8段，每段16位)

### 端口
* 在网络上有很多电脑，这些电脑一般运行了多个网络程序。每种网络程序都打开一个Socket，并绑定到一个端口上，不同的端口对应于不同的网络程序。
* 常用端口：21 FTP ,25 SMTP ,110 POP3 ,80 HTTP , 443 HTTPS

### 有两种常用Socket类型：
* 流式Socket（STREAM）：是一种面向连接的Socket，针对于面向连接的TCP服务应用，安全，但是效率低
* 数据报式Socket（DATAGRAM）：是一种无连接的Socket,对应于无连接的UDP服务应用.不安全(丢失,顺序混乱,在接收端要分析重排及要求重发),但效率高.

## Socket定义

* Socket的英文原义是“孔”或“插座”。作为进程通信机制，取后一种意思。通常也称作“套接字”，用于描述IP地址和端口，是一个通信链的句柄。(其实就是两个程序通信用的。)

* Socket非常类似于电话插座。以一个电话网为例。电话的通话双方相当于相互通信的2个程序，电话号码就是IP地址。任何用户在通话之前，首先要占有一部电话机，相当于申请一个Socket；同时要知道对方的号码，相当于对方有一个固定的Socket。然后向对方拨号呼叫，相当于发出连接请求。对方假如在场并空闲，拿起电话话筒，双方就可以正式通话，相当于连接成功。双方通话的过程，是一方向电话机发出信号和对方从电话机接收信号的过程，相当于向Socket发送数据和从Socket接收数据。通话结束后，一方挂起电话机相当于关闭Socket，撤消连接。

* 人通过【电话】可以通信

* 程序通过【Socket】来通信。

* 套接字 就是 程序间的 电话机。

## Socket流式(服务器端和客户端)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image5.png)

* 1.服务端welcoming socket 开始监听端口(负责监听客户端连接信息)
* 2.客户端client socket连接服务端指定端口(负责接收和发送服务端消息)
* 3.服务端welcoming socket 监听到客户端连接，创建connection socket。
  (负责和客户端通信)

### 服务器端的Socket(至少需要两个)

* 一个负责接收客户端连接请求(但不负责与客户端通信)
* 每成功接收到一个客户端的连接便在服务端产生一个对应的负责通信的Socket在接收到客户端连接时创建.
* 为每个连接成功的客户端请求在服务端都创建一个对应的Socket(负责和客户端通信).

### 客户端的Socket

* 客户端Socket,必须指定要连接的服务端IP地址和端口。
* 通过创建一个Socket对象来初始化一个到服务器端的TCP连接

## Socket的通讯过程

### 服务器端：
* 申请一个socket
* 绑定到一个IP地址和一个端口上
* 开启侦听，等待接授连接
* 服务器端接到连接请求后，产生一个新的socket(端口大于1024）与客户端建立连接并进行通讯，原监听socket继续监听。

### 客户端：
* 申请一个socket
* 连接服务器（指明IP地址和端口号）

## Socket的构造函数

### 连接通过构造函数完成。

```c#
public Socket(AddressFamily addressFamily, SocketType socketType, ProtocolType protocolType)
```
* AddressFamily 成员指定 Socket 用来解析地址的寻址方案。例如，InterNetwork 指示当 Socket 使用一个 IP 版本 4 地址连接。
* SocketType 定义要打开的 Socket 的类型
* Socket 类使用 ProtocolType 枚举向 Windows Sockets API 通知所请求的协议

常用构造函数

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image6.png)

## Socket方法

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image7.png)

注意事项:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image8.png)

## Socket通信基本流程图

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image9.png)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image10.png)

## 传输协议

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image11.png)

## 扩展

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/Socket/Socket/images/Image12.png)

# TCP聊天室示例

## 创建服务器（在VS2013中）

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Net;
using System.Net.Sockets;

namespace Tcp_Server
{
    class Program
    {
        private static List<Client> clientList = new List<Client>();
        static void Main(string[] args)
        {
            //创建Socket
            Socket soket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
            //绑定IP和端口
            IPAddress address = IPAddress.Parse("192.168.2.118");
            IPEndPoint point = new IPEndPoint(address, 9090);
            soket.Bind(point);
            Console.WriteLine("服务器启动成功");
            //监听客户端数量
            soket.Listen(30);
            Console.WriteLine("服务器开始监听");
            while(true)
            {
                Socket newsocket = soket.Accept();  //返回一个客户端的Socket；
                Console.WriteLine("服务器连接一个新的客户端：" + newsocket.LocalEndPoint);
                Client client = new Client(newsocket);
                clientList.Add(client);
            }                                
        }
        //广播消息
        public static void BroadcastMessage(string msg)
        {
            //创建一个集合，用来存放连接断开的客户端
            List<Client> notConnectList = new List<Client>();
            for (int i = 0; i < clientList.Count; i++)
            {
                if(clientList[i].Connected == true)
                {
                    clientList[i].SendMessage(msg);
                }
                else
                {
                    notConnectList.Add(clientList[i]);
                }
            }
            //将断开的客户端从开始连接进来的客户端的集合中删除
            for (int i = 0; i < notConnectList.Count; i++)
            {
                clientList.Remove(notConnectList[i]);
            }
        }
        
    }
}
```
### 在这个控制台项目上再添加一个类

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Net.Sockets;
using System.Threading;

namespace Tcp_Server
{
    class Client
    {
        private Socket tcpClientSocket;
        private Thread thread;
        private byte[] data = new byte[2048];
        //添加一个属性，用来判断是否断开连接
        public bool Connected
        {
            get { return tcpClientSocket.Connected; }
        }
        public Client(Socket tcpsocket)
        {
            tcpClientSocket = tcpsocket;
            //开启一个线程，处理客户端的数据接收
            thread = new Thread(ReceiveMessage);
            thread.Start();
        }
        //接收消息
        private void ReceiveMessage()
        {
            //一直在不断的接收客户端的数据
            while(true)
            {
                //在接收数据之前判断一下Socket连接是否断开
                //10毫秒的响应时间，可以读取数据的话，如果返回true，表示连接断开
                if(tcpClientSocket.Poll(10,SelectMode.SelectRead))
                {
                    tcpClientSocket.Close();
                    break;
                }
                int length = tcpClientSocket.Receive(data);
                string message = Encoding.UTF8.GetString(data, 0, length);
                Program.BroadcastMessage(message);
                Console.WriteLine("收到了来自" + tcpClientSocket.LocalEndPoint + "的新消息：" + message);
            }
        }
        public void SendMessage(string msg)
        {
            byte[] data1 = Encoding.UTF8.GetBytes(msg);
            tcpClientSocket.Send(data1);
        }        
    }    
}
```

## 创建客户端（在Unity中）

UI界面图如下：

![](http://i2.tiimg.com/1949/0530ced8f7078116.png)

代码如下：

```c#
using UnityEngine;
using System.Collections;
using UnityEngine.UI;
using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Threading;

public class TcpClientToServer : MonoBehaviour {

    private Button btn_Send;
    private Button btn_cServer;
    private Text chattext;
    private InputField inputText;
    Socket socket;
    private byte[] data = new byte[2048];   //接收消息的字节
    private Thread thread;    //线程
    private string message;  //接收消息的容器；
    void Start()
    {
        chattext = transform.Find("Panle/chatText").GetComponent<Text>();
        inputText = transform.Find("InputText").GetComponent<InputField>();
        btn_Send = transform.Find("btn_send").GetComponent<Button>();
        btn_Send.onClick.AddListener(C2SsendMessage);
        btn_cServer = transform.Find("ConnectServer").GetComponent<Button>();
        btn_cServer.onClick.AddListener(OnConnectServer);
    }
	
    void OnConnectServer()
    {
        IPAddress ip = IPAddress.Parse("192.168.2.118");
        //创建Socket
        socket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
        //连接服务器
        EndPoint point = new IPEndPoint(ip, 9090);
        socket.Connect(point);
        print("连接服务器成功。");
        thread = new Thread(ReceiveMessage);
        thread.Start();
    }
    //向服务器发送消息
	void C2SsendMessage()
    {
        string send = inputText.text;
        byte[] data = Encoding.UTF8.GetBytes(send);
        socket.Send(data);
        inputText.text = "";
    }
    // 接收消息
    void ReceiveMessage()
    {
        while(true)
        {
            if(socket.Connected == false)            //断开连接跳出循环
            {
                break;
            }
            else
            {
                int length = socket.Receive(data);
                message = Encoding.UTF8.GetString(data, 0, length);  //接收到的消息
            }
        }
    }
	// Update is called once per frame
	void Update () {
	    if(message != null && message != "")
        {
            chattext.text += message + "\n";  //判断当接收的消息不为空时，将消息传给聊天面板
            message = "";   //清空接收消息的字符串
        }
	}
}
```









