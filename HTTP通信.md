# Uniyt3D-

## HTTP概念
超文本传输协议（HTTP，HyperText Transfer Protocol）是互联网上应用最为广泛的一种网络协议。所有的WWW文件都必须遵守这个标准。

## HTTP请求响应模型

1.HTTP是一个客户端和服务器端请求和应答的标准

2.通过HTTP或者HTTPS协议请求的资源由统一资源标识符（Uniform Rsource Identifiers）（或者更准确一些，URLs）来标识。

3.我们在浏览器的地址栏里输入的网站地址叫做URL(Uniform Resource Locator，统一资源定位符)。就像每家每户都有一个门牌地址一样，每个网页也都有一个Internet地址。当你在浏览器的地址框中输入一个URL或是点击一个超级链接时，URL就确定了要浏览的地址。浏览器通过超文本传输协议（HTTP），将Web服务器上站点的网页代码提取出来，并翻译成漂亮的网页

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http/images/20161215215617.jpg)

__HTTP协议永远都是客户端发起请求，服务器端回送响应__

## 常用请求方式

GET和POST是HTTP协议所规定的两种通讯方式（客户端向服务器传递数据的两种方式）

### GET

把数据放到HTTP协议的URL里，最多只能传输1024个字节。
格式：
```
http://127.0.0.1:80/1405A/test.php ?name=testUser&pwd=123
```
特点：
安全性低，传输量小，速度快

### POST
以表单提交数据，数据在HTTP的协议体中，理论上没有传输数据的最大限制。

特点：
数据量大，安全性较高

## POST和GET对比

#### GET

优点：便于测试，简洁明了
缺点：信息量比较小，安全性相对低

#### POST

优点：信息量大，安全性相对高
缺点：测试不太方便

## 通过网页来认识HTTP请求

我们通过模拟用户登录操作，来演示Get请求与post请求的不同。由于采用的服务器端为php语言，所以我们需要安装一个支持php的web服务器。

下载地址:http://www.wampserver.com/

具体的WampServer安装过程请参阅:
http://jingyan.baidu.com/article/2d5afd69efe9cf85a3e28e54.html

【案例】GET请求
1.创建一个能够输入用户名和密码的html页面login_get.html，本次案例采用GET方式请求

```c#
<html>
<head>
  <meta charset="utf-8">
  <title>模拟用户登录</title>
</head>
<body>
  <span>模拟用户登录GET</span>

  <!--
  创建一个表单，用于向服务器传递用户名和密码、

  form为表单对象
  action对应的表单需要由哪个网页处理
  method 数据请求的方式
  -->
  <form action="login_get.php" method="get">    //action表示的是返回php文件名，method表示传输请求类型
     <span>账号: <input type="text" value=""  id="username" name="username"></span><br />
     <span>密码: <input type="password" value=""  id="password" name="password"></span><br />
     <input type="submit" value="登录"/>
  </form>
</body>
<html>
```

1.将编写好的文件，复制到wamp安装目录下的www文件夹中，通过浏览器访问此文件。
http://localhost/login.html

2.网页效果如下：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http/images/20161229213924.jpg)

3.接下来，再编写服务器端PHP脚本，用来接收html网页传递过来的用户名和密码，经过处理后，输出一些提示信息。

4.login_get.php脚本如下：

```c#
<?php
//接收传递过来的变量name
  $name=$_GET["username"];  //GET表示传输类型

//接收到的密码
  $pwd=$_GET["password"];

  echo  "用户名是".$name.","."密码是:".$pwd."<br/>";
  if($name=="admin"){
    if($pwd=="123"){
      echo "欢迎管理员登录!";
    }else{
      echo "密码不正确，回去想想吧！";
    }
  }else{
    echo "普通用户，我也不知道密码对不对！";
  }
?>
```

5.将编写好的login.php文件放置在login.html相同目录下。

当我们在html网页中随意输入一些用户名和密码时，点击登录按钮会自动将用户名和密码传递到login.php来处理，并将处理结果显示在网页中。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http/images/20161229214418.jpg)

我们可以看到，在网页的地址栏中会显示成下面这样，这种请求方式便是GET请求的效果。
```
http://localhost/login_get.php?username=admin&password=123
```

【案例POST请求】

当采用POST方式传递数据时，需要将表单中的 method属性更改为post。

1.POST请求的表单项中，需要将form的method设置为post.

login_post.html
```c#
<html>
<head>
  <meta charset="utf-8">
  <title>模拟用户登录</title>
</head>
<body>
  <span>模拟用户登录 POST</span>

  <!--
  创建一个表单，用于向服务器传递用户名和密码、

  form为表单对象
  action对应的表单需要由哪个网页处理
  method 数据请求的方式
  -->
  <form action="login_post.php" method="post">
     <span>账号: <input type="text" value=""  id="username" name="username"></span><br />
     <span>密码: <input type="password" value=""  id="password" name="password"></span><br />
     <input type="submit" value="登录"/>
  </form>
</body>
<html>
```
2.既然请求方式已经修改为post，那么服务器端接收也需要修改接收方式。

login_post.php
```c#
<?php

//接收传递过来的变量name
  $name=$_POST["username"];

//接收到的密码
  $pwd=$_POST["password"];

  echo  "用户名是".$name.","."密码是:".$pwd."<br/>";
  if($name=="admin"){
    if($pwd=="123"){
      echo "欢迎管理员登录!";
    }else{
      echo "密码不正确，回去想想吧！";
    }
  }else{
    echo "普通用户，我也不知道密码对不对！";
  }

?>
```

3.此种请求方式不会在浏览器的地址栏上显示出表单里的内容，但内容的确传递过来了。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http/images/20161229215401.jpg)


# Unity中使用HTTP

## 认识Unity中的www
WWW是一个Unity开发中非常常用到的工具类，主要提供一般Http访问的功能，以及动态从网上下载图片、声音、视频Unity资源等。

主要支持的协议有:
* http://
* https://
* file://
* ftp://  (只支持匿名账号)

其中file://便是访问本地文件。

## WWW加载网络资源

这里指的网络资源指图片，文本，视频，音频等各种格式的资源。实际上WWW类具有很多实用的属性和资源对应，如下：
* assetbundle:
AssetBundle的数据流，可以包含项目文件夹中的任何类型资源。
* audioClip(声音)
从下载的数据，返回一个AudioClip。（只读）
* bytes(字节数组)
以字节组的形式返回获取到的网络页面中的内容(只读)。
* movie(视频)
从下载的数据，返回一个MovieTexture（只读）。
* text(文本,XML,Json)
通过网页获取并以字符串的形式返回内容(只读)。
* texture(图片)
从下载的数据返回一个Texture2D

## 使用WWW实现资源加载

在上面提到的所有资源，加载的思路都是一样的，所以这里我们通过加载图片为例来学习资源的加载。

#### 图片加载
首先得到图片的网络地址，现需要将此图片加载到Unity，并显示到界面上
示例图片地址：
https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png

1.使用UGUI在界面上添加一个RawImage组件，并创建一个LoadTexture.cs文件

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http%E5%9C%A8Unity%E4%B8%AD%E4%BD%BF%E7%94%A8/images/20170116131040.jpg)

2.在LoadTexture.cs中编写下面的代码

```c#
using UnityEngine;
using System.Collections;
using UnityEngine.UI;

public class LoadTexture : MonoBehaviour {
    // 图片地址
    private string url = "https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png";
    private RawImage img;
	
	void Start () {
        //获取RawImage组件
        img = this.transform.FindChild("RawImage").GetComponent<RawImage>();
        StartCoroutine(DoLoad());
	}

    IEnumerator DoLoad()
    {
        WWW www = new WWW(url);
        //挂起程序段，等资源下载完成后，继续执行下去  
        yield return www;

        //判断是否有错误产生  
        if (string.IsNullOrEmpty(www.error))
        {
            //把下载好的图片显示到RawImage中  
            img.texture = www.texture;
            //释放资源  
            www.Dispose();
        }
    }
}
```

__注意__:加载的音乐的格式不可以为mp3格式
3.程序运行后效果

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http%E5%9C%A8Unity%E4%B8%AD%E4%BD%BF%E7%94%A8/images/20170116131544.jpg)

## WWW实现GET请求

在上节课程内容中，我们已经编写的用于模拟登录的GET方式页面，此案例将通过WWW在Unity客户实现Get请求。
1.编写Unity客户端代码，用于模拟GET请求。

```c#
using UnityEngine;
using System.Collections;

public class HttpGetDemo : MonoBehaviour
{

    //用于处理GET请求的页面地址
    private string url = "http://localhost/login_get.php?username=admin&password=123";

    // Use this for initialization
    void Start()
    {
        StartCoroutine(DoLoad());
    }


    IEnumerator DoLoad()
    {
        WWW www = new WWW(url);
        yield return www;

        //判断是否有错误产生  
        if (string.IsNullOrEmpty(www.error))
        {
            //输出服务器返回的内容
            print(www.text);

        }
    }
}
```
2.服务器返回结果

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/Http%E5%9C%A8Unity%E4%B8%AD%E4%BD%BF%E7%94%A8/images/20170116135746.jpg)

## WWW实现POST请求

在Unity中实现POST请求稍与GET有一些不同，地址中，只需要指定需要请求的页面地址即可，需要传递的参数通过WWWForm来进行构建。

1.同样，使用上节课中的服务器页面，编写客户端程序。
```c#
using UnityEngine;
using System.Collections;

public class HttpPostDemo : MonoBehaviour
{

    //用于处理GET请求的页面地址
    private string url = "http://localhost/login_post.php";

    // Use this for initialization
    void Start()
    {
        StartCoroutine(DoLoad());
    }


    IEnumerator DoLoad()
    {
        //创建WWWForm对象
        WWWForm form = new WWWForm();
        //添加内容
        form.AddField("username", "admin");
        form.AddField("password", "123");

        //通过地址，表单构建WWW对象
        WWW www = new WWW(url,form);

        yield return www;

        //判断是否有错误产生  
        if (string.IsNullOrEmpty(www.error))
        {
            //输出服务器返回的内容
            print(www.text);

        }
    }
}

```
2.返回地结果与GET请求无任何差异。

![](/static/k25/03_引擎高级进阶/数据处理及HTTP应用/Http在Unity中使用/images/20170116135746.jpg)






















