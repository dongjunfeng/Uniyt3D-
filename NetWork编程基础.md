# Uniyt3D-
## NetWroke介绍
UnityEngne.Network是实现网络功能的核心之一,提供了基本的功能函数，例如建立服务器和加入服务器等。首先进行函数的介绍，然后通过一个案例讲解如何使用这些函数。

### 函数介绍

```
Network.InitializeServer(int connettions,int Port,bool useNat); 
```
该函数用于初始化服务器。Connections是最大连接数, Port是服务器监听的端口号,useNat表明是否使用Nat穿透。返回枚举类型NetworkConnectionErrer.返回NetworkConnectionError.NoError时表示创建服务器成功，没有错误.

```
Network.Connect(string IP,int Port);
```
该函数用于连接服务器，IP是所要连接的服务器的IP地址，Port是端口号。返回枚举类型NetworkConnectionError.返回NetworkConnetionError.NoError是表示连接服务器成功.没有错误.

```
Network.Disconnect();
```
该函数用于断开网络连接。如果是服务器的话，则是断开网络连接并连接服务器。

下面代码是一个简便的创建服务器，连接服务器
```c#
using UnityEngine;
using System.Collections;
using UnityEngine.UI;
using UnityEngine.Events;

public class NetWrokeDemo : MonoBehaviour {

    public Button btn_Server;
    public Text Server_Text;
    public Button btn_Client;
    public Text Client_Text;
    public Text Connect;

    public bool isServer = false;
    public bool isClient = false;

    public Text SendText;
    public InputField sendinput;
    public Button btn_send;

    public NetworkView networkview;
    void Awake()
    {
        networkview = GetComponent<NetworkView>();
    }
	// Use this for initialization
	void Start () {
        btn_Server = GetByName("btn_Server").GetComponent<Button>();
        Server_Text = btn_Server.gameObject.GetComponentInChildren<Text>();
        btn_Server.onClick.AddListener(OnServerClick);
        btn_Client = GetByName("btn_Client").GetComponent<Button>();
        Client_Text = btn_Client.gameObject.GetComponentInChildren<Text>();
        btn_Client.onClick.AddListener(OnClientClick);

        Connect = GetByName("Connect").GetComponent<Text>();
        SendText = GetByName("SendText").GetComponent<Text>();
        sendinput = GetByName("SendInputField").GetComponent<InputField>();
        btn_send = GetByName("btn_send").GetComponent<Button>();
        btn_send.onClick.AddListener(SendMessage);

	}
  //点击按钮创建服务器
	void OnServerClick()
    {
        isServer = !isServer;
        if(isServer)
        {
        //                               初始化服务器             允许连接人数，端口号
            NetworkConnectionError err = Network.InitializeServer(10, 9091, false);
            if(err == NetworkConnectionError.NoError)
            {
                print("创建服务器成功");
                Server_Text.text = "断开服务器";
            }
        }
        else
        {
            Network.Disconnect();
            print("断开服务器成功");
            Server_Text.text = "创建服务器";
        }
    }
    //当客户端连接上服务器时，在服务器上调用这个函数
    void OnPlayerConnected(NetworkPlayer player)
    {
        print("当前连接IP为：" + player.ipAddress + "端口为:" + player.port);
    }
    //当客户端断开连接时，在服务器上调用这个函数
    void OnPlayerDisconnected(NetworkPlayer player)
    {
        print("端口为:" + player.port + "玩家已经断开连接");
    }
//点击按钮连接服务器
    void OnClientClick()
    {
        isClient = !isClient;
        if(isClient)
        {
        //                                              连接服务器的IP，端口号
            NetworkConnectionError err = Network.Connect("192.168.2.107", 12345);
            if(err == NetworkConnectionError.NoError)
            {
                print("已经连接服务器");
                Client_Text.text = "断开连接";
            }
        }
        else
        {
            Network.Disconnect();
            print("断开成功");
            Client_Text.text = "连接服务器";
        }
    }
    //当客户端成功连接服务器，在客户端调用这个函数
    void  OnConnectedToServer()
    {
        Connect.text = "连接服务器数量：" + Network.connections.Length;        
        print("成功连接上服务器");
    }
    //当客户端断开服务器时，在客户端调用这个函数
	void  OnDisconnectedFromServer()
    {
        print("已经断开服务器");
    }
	void Update () {
        Connect.text = "连接服务器数量：" + Network.connections.Length;
        SendText.text = sendtemp;
    }
	GameObject GetByName(string name)
    {
         Transform[] trs = GetComponentsInChildren<Transform>();
         for (int i = 0; i < trs.Length; i++)
	     {
		    if(trs[i].name == name)
            {
               return trs[i].gameObject;
             }
		    }return null;
     }
	void SendMessage()
    {
        networkview.RPC("Send", RPCMode.All, sendinput.text);
        sendinput.text = "";
    }
    public string sendtemp;
    [RPC]
    public void Send(string input)
    {
        sendtemp += input + "\n";
    }
}
```

效果图如下

![](http://i1.ciimg.com/1949/aa343e3af85e1eac.png);
