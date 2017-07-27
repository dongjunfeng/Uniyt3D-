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


## 实例一：简易聊天室

首先创建UI如下所示：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/NetWorkView/images/Image.png)
![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/NetWorkView/images/Image1.png)
![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/Socket%E9%80%9A%E4%BF%A1/NetWorkView/images/Image2.png)

然后添加代码如下：
__注意__:按钮是手动添加方法，所以没有写按钮的注册方法，还要记得在Canvas上添加脚本时，添加一个NetworkView组件。
```c#
using UnityEngine;
using System.Collections;
using System.Collections.Generic;
using UnityEngine.UI;
public class NetworkViewChatTest : MonoBehaviour
{

    private string IP = "192.168.2.118";          //本地IP
    private int Port = 1000;

    private NetworkView networkView;
    private string myName = "";        //名字
    private string textRecord = "";  //聊天消息记录
    private string textToSend = "";   //将要发送的消息

    private Dictionary<string, string> manlist = new Dictionary<string, string>(); //NetworkViewID以及名字的字典;
    private List<string> names = new List<string>();//聊天室当前人员名字的链表

    bool isChat = false;    //控制是否可以聊天

    public GameObject obj;    //获取组件需要

    public Image ChatPanel, CreatePanel;       //聊天面板，创建面板
    public InputField NameInputField, ChatInputField; //名字输入框，聊天内容输入框
    public Text DisconnectText, CutClientNum, ChatTlak, NameChat; // 关闭聊天室按钮的Text,当前在线人员的数量,聊天室人员名称


    void Awake()
    {
        networkView = GetComponent<NetworkView>();
    }
    void Start()
    {
        obj = GetByName("ChatInputField");
        if (obj != null)
        {
            ChatInputField = obj.GetComponent<InputField>();
        }

        obj = GetByName("NameChat");
        if (obj != null)
        {
            NameChat = obj.GetComponent<Text>();
        }

        obj = GetByName("ChatTlak");
        if (obj != null)
        {
            ChatTlak = obj.GetComponent<Text>();
        }
        obj = GetByName("CutClientNum");
        if (obj != null)
        {
            CutClientNum = obj.GetComponent<Text>();
        }
        obj = GetByName("DisconnectText");
        if (obj != null)
        {
            DisconnectText = obj.GetComponent<Text>();
        }

        obj = GetByName("ChatPanel");
        if (obj != null)
        {
            ChatPanel = obj.GetComponent<Image>();
            ChatPanel.gameObject.SetActive(false);
        }
        obj = GetByName("CreatePanel");
        if (obj != null)
        {
            CreatePanel = obj.GetComponent<Image>();
        }
        obj = GetByName("NameInputField");
        if (obj != null)
        {
            NameInputField = obj.GetComponent<InputField>();
        }       
    }

    // Update is called once per frame
    void Update()
    {
        if (isChat)  //可以聊天时候的处理
        {
            ChatTlak.text = textRecord;
            string txt = "";
            foreach (var s in names)
            {
                txt += s + "\n";
            }
            NameChat.text ="当前聊天室的人有：" + "\n"+ txt;
            textToSend = ChatInputField.text;
        }
        else   //默认记录名字
        {
            myName = NameInputField.text;
        }
    }
    public void SendButton()  //发送消息按钮
    {        
        networkView.RPC("SendText", RPCMode.All, myName + ":" + textToSend);
        ChatInputField.text = "";
    }
    public void DisconnectButton()  //关闭聊天室和离开聊天室按钮
    {
        CreatePanel.gameObject.SetActive(true);
        ChatPanel.gameObject.SetActive(false);
        Network.Disconnect();
        isChat = false;
    }
    public void ClientConnect()// 客户端连接
    {

        NetworkConnectionError error = Network.Connect(IP, Port);
        if (error == NetworkConnectionError.NoError)
        {
            DisconnectText.text = "离开聊天室";
            CreatePanel.gameObject.SetActive(false);
            ChatPanel.gameObject.SetActive(true);
            isChat = true;
            CutClientNum.text = "当前连接人数：" + Network.connections.Length;
            print("连接成功");
        }

    }
    void OnConnectedToServer()//连接服务器
    {
        Debug.Log("连接到服务器");
        networkView.RPC("Server_Join", RPCMode.Server, myName);
    }
    void OnPlayerDisconnected(NetworkPlayer player)//当客户端断开服务器时被调用的函数
    {
        string id = player.ToString();
        Debug.Log(id + "离开");
        if (manlist.ContainsKey(id))
        {
            networkView.RPC("SendText", RPCMode.All, manlist[id] + "离开了聊天室");
            manlist.Remove(id);
        }
        Server_UpdateNameList();
    }
    public void CreateServer()//创建一个服务器
    {

        NetworkConnectionError error = Network.InitializeServer(10, Port, false);
        if (error == NetworkConnectionError.NoError)
        {
            DisconnectText.text = "关闭聊天室";
            CreatePanel.gameObject.SetActive(false);
            ChatPanel.gameObject.SetActive(true);
            manlist.Add(Network.player.ToString(), myName);
            Server_UpdateNameList();
            isChat = true;
            CutClientNum.text = "当前连接人数：" + Network.connections.Length;

            print("创建成功");

        }

    }
    void Server_UpdateNameList()//服务器向客户端发送人员名单及聊天记录,供客户端更新显示
    {
        string textToSend = "";
        foreach (var item in manlist)
        {
            textToSend += item.Value + "|";
        }
        CutClientNum.text = "当前连接人数：" + Network.connections.Length;

        networkView.RPC("RPC_GetNameList", RPCMode.All, textToSend);
        networkView.RPC("RPC_ChatRecordUpdate", RPCMode.All, textRecord);
    }
    [RPC]//人员名单
    public void RPC_GetNameList(string content, NetworkMessageInfo info)
    {
        string[] ss = content.Split('|');
        names.Clear();
        names.AddRange(ss);
    }
    [RPC]//聊天记录
    public void RPC_ChatRecordUpdate(string content)
    {
        textRecord = content;
    }
    [RPC]//当客户端连接成功时向服务器发送的消息
    public void Server_Join(string client_name, NetworkMessageInfo info)
    {
        string id = info.sender.ToString();
        Debug.Log("Joined:" + id);
        networkView.RPC("SendText", RPCMode.All, client_name + "加入了聊天室");
        manlist.Add(id, client_name);
        Server_UpdateNameList();
    }
    [RPC]//发送文本
    public void SendText(string content, NetworkMessageInfo info)
    {
        textRecord += content + "\n";
    }
    GameObject GetByName(string name)//寻找物体的方法
    {
        Transform[] trs = GetComponentsInChildren<Transform>();
        for (int i = 0; i < trs.Length; i++)
        {
            if (trs[i].name == name)
            {
                return trs[i].gameObject;
            }
        }
        return null;
    }
}

```


