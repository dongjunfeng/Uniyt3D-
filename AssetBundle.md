# Uniyt3D-

## 什么是AssetBundle资源打包？

### AssetBundle：
是一种Unity导出的包括资源的文件。这些文件使用一个专用的压缩格式,应用程序可以根据需要加载。允许用流读取模型、纹理、音频剪辑,甚至整个场景等内容,分别从资源包中使用他们。AssetBundles设计简化内容下载到您的应用程序。AssetBundles可以包含任何类型的资产类型被统一,由文件名扩展。如果你想要包括的文件自定义二进制数据,他们应该扩展“.bytes”。统一将作为TextAssets导入这些文件。

## AssetBundle的工作流程

### AssetBundle的典型的工作流程

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image1.png)

在开发过程中,开发人员需要准备AssetBundles资源和上传到服务器

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image2.png)

在工作时，开发人员也可根据需求在服务器上加载自己所需的AssetBundles资源，然后应用到自己的应用程序当中。

## 如何打包AssetBundle资源

### BuildingAssetBundles in Unity5.x ：
在Unity4.x中AseetBundler使用编辑器创建脚本。为了简化这一过程Unity5.x编辑器包 括AseetBundler创建工具。现在,如果你选择一个资源在编辑器的底部会出现一个下拉Inspector窗口，您可以将指定的资源包(如果有的话)应该打包成资源。默认情况下资源包选项设置为None,这意味着资源不会被写进一个资源包。您可以创建新的资源包,给它们命名,然后使用这些新资源包的名字作为资源的目的地。
创建资源包,资源包的名字总是小写。如果你使用大写字符的名字他们将转换为小写。使用正斜杠的名字定义资源包有效地创建文件夹,菜单会有子菜单，如果您创建资源包没有资源分配给他们,那么可以使用“删除未使用的名称”选项。这将删除空的资源包。

### AssetBundle打包
这里以Android平台为例，首先将平台转为Android。点击导航菜单-File-Build Settings,打开Build设置窗口，在Platform栏选中Android SDK.在Player Settings中的Other Settings栏设置PlayerSettings.bundleIdentifier,这里设置为com.myproject.project.

#### 1.资源指定

新建一个场景，命名为16.2.26.在Project窗口中新建一个Material,命名为16.2.26 .Mat，并设置Albedo主贴图为16.2.26 .Tex。再新建一个Cube，命名为16.2.26 .Cube,并将16.2.26 .Cube拖拽至Project窗口创建预制体。
选中16.2.26.Cube,在Inspector窗口的最下方有一个栏AssetBundle,此栏用于设置哪些资源将导出AssetBundle包，如图下图所示：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image3.pnghttps://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image3.png)

点击None下拉菜单按钮，然后点击“New…”按钮，在输入栏里填写cube并按回车。这是告诉Unity这个资源需要打包到名为cube的AssetBundle里。同样，请为16.2.26.Mat和16.2.26.Cube,Text做同样的设置。

#### 2.AssetBundle文件生成

AseetBundle文件的生成是通过UnityEditor.BuildPipeline类的BuildAssetBundles()函数完成的。
在16.2.26文件夹下新建文件夹并命名为Editor(因为使用UnityEditor功能的脚本必须位于名为Editor的文件夹下)，
在该文件夹下新建脚本并命名为C_16.2.26,
脚本如下图所示:

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image4.png)

也可以这样创建
```c#
using UnityEngine;
using System.Collections;
using UnityEditor;

public class AssetbundleDemo : MonoBehaviour {

	[MenuItem("Build/ModelAsset")]     //菜单栏显示
    static void BundleAssetMain()
    {   
        //输出路径
        string path = Application.dataPath;
        //打包的资源
        AssetBundleBuild[] AssetBundles = new AssetBundleBuild[1];
        //打包的文件名称
        AssetBundles[0].assetBundleName = "Terrainmodle";
        //要打包预设体路径名称
        string[] AssetName = new string[1] { "Assets/Prefab/Terrain.prefab"};

        AssetBundles[0].assetNames = AssetName;
        //构建AssetBundles文件的方法                      //选择资源包的关系类型                           //打包的目标平台
        BuildPipeline.BuildAssetBundles(path,AssetBundles,BuildAssetBundleOptions.DeterministicAssetBundle,BuildTarget.StandaloneWindows64);
    }
}
```
## 如何上传AseetBundle资源

接下来，就是把打好的资源包上传至服务器。这里我们使用WAMP在Windows系统下搭建一个
简单的服务器。
下载WAMP并安装。在安装完成后你需要设置一下默认浏览器，选择桌面的Internet或者他浏览器完成安装。运行WAMP，屏幕右下角的W图标即是WAPA软件，右键点击WAMP图标-language-chinese,可将语言设置为中文。
左键点击WAMP图标-启动所有服务，开启服务器。左键点击WAMP图标-切换到在线状态。
左键点击WAMP图标-www目录，新建一个文件夹并命名为Unity,拖入一张图片（这里以link.png为例）。
注意：如果图标没有变成绿色，右击计算机点击管理，然后点击服务，将安装的本地服务器MySQL改成手动
打开浏览器，输入http://127.0.0.1/Unity/link.png并按回车，浏览器中显示了我们刚刚上传的图片，如图下图所示。127.0.0.1是本机IP地址，后面的路径则是www文件夹下的路径。将ABs文件夹复制至www下的Unity文件夹。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image5.png0)

## 如何下载AssetBundle

新建一个场景并命名为，16.2.26.3，新建一个空的游戏对象并命名为WWWManager,为其添加代码。代码如下：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86%E5%8F%8AHTTP%E5%BA%94%E7%94%A8/AssetBundle/images/Image6.png)

代码也可以这样写

```c#
using UnityEngine;
using System.Collections;

public class LoadAssetBundle : MonoBehaviour {

    public string url = "http://localhost/Unity/terrainmodle";
    void Start()
    {
        StartCoroutine(LoadABs(url));
    }
    IEnumerator LoadABs(string url)
    {
        WWW www = new WWW(url);

        yield return www;

        if(www.isDone)
        {
            GameObject clone = www.assetBundle.LoadAsset("terrain.prefab") as GameObject;
            GameObject.Instantiate(clone);
        }
        www.Dispose();
    }
}
```

WWW.LoadFromCacheOrDownload();这个下载函数是AssetBundle专用的，可以很方便地处理AssetBundle文件的版本更新。在通过此函数下载AssetBundle后，资源会被缓存至本地储存起来；在下次调用此函数时，如果AssetBundle有新版本则下载新版本，如果没有新版本则不下载而直接从本地读取。
缓存的资源可以通过Caching.CleanCache()函数全部删除。



