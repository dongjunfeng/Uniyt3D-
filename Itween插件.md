# Uniyt3D-
## iTween基本介绍

iTween是一个动画库,作者创建它的目的就是最小的投入实现最大的产出.让你做开发更轻松,用它可以轻松实现各种动画,晃动,旋转,移动,褪色,上色,控制音频等等

## iTween基本原理

iTween的核心是数值插值，简单说就是给iTween两个数值(开始值，结束值)，它会自动生成一些中间值，大概像这样子, 开始值->中间值 -> 中间值 …. -> 结束值。
这里的数值可以理解为: 数字，坐标点，角度，物体大小，物体颜色，音量大小 等

## iTween的下载地址
```c#
官网：http://itween.pixelplacement.com
```

## iTween 类介绍
iTween类的公共操作接口均以静态方法的形式提供。
可分为三大类：

* 1.静态注册方法：提供注册动画效果的静态方法接口。如：MoveTo、CameraFadeTo等。

* 2.Update静态方法：提供每帧改变属性值的环境，在Update或循环环境中调用。如：MoveUpdate、AudioUpdate等。

* 3.外部工具方法：包括动画控制、路径绘制等。
iTween类内部定义了三种枚举类型：

* 1.EaseType：缓动类型枚举
* 2.LoopType：动画的循环类型枚举
* 3.NamedValueColor:已命名颜色枚举

## 主要功能介绍
八种实现动画方法：

* 1.Fade：淡入淡出
```c#              
iTween.FadeTo(gameObject, Alpha,time);
gameObject: 一个带有GUIText组件的字或者带有GUITexture贴图的物体
Alpha：透明度（0--1）
time：变换到该透明度所需时间
iTween.FadeTo(gameObject,iTween.Hash("time",2f.....);

```
* 2.Look：旋转对象使其面朝指定位置

```c#
iTween.LookTo(this.gameObject, go.transform.position, 2f);
//使物体在2s时间内看向其他物体或者坐标
iTween.LookFrom(this.gameObject, go.transform.position, 2f);
//使物体在运行时候看向其他物体或坐标，然后再2s时间内转回原来的位置
```

* 3.Move：移动位置，

```c#
 iTween.MoveAdd(this.gameObject, new Vector3(0, 0, 1), 2f);
//使物体移动到该坐标点
 iTween.MoveBy(this.gameObject, new Vector3(0, 0, 1), 2f);
 //使物体移动到该坐标点，和MoveAdd感觉差不多
iTween.MoveTo(this.gameObject, new Vector3(0, 0, 1), 2f);
//使物体移动到该坐标点，可以到达（0,0,1）而MoveBy只能到达一个近似值
iTween.MoveFrom(this.gameObject, new Vector3(0, 0, 1), 2f);
//使物体从（0,0,1）返回物体起始位置

* 4.Rotate：旋转指定欧拉角度

```c#
 iTween.RotateTo(this.gameObject, new Vector3(0, 0,1) * 180, 2f);
 //目标沿着Z轴在2s旋转180度
 ```
 
 * 5.Scale：缩放大小
 ```c#
iTween.ScaleTo(this.gameObject, new Vector3(5, 5, 1), 2f);
//使物体的体积大小在2s内变为（5,5,1）；
iTween.ScaleFrom(this.gameObject, new Vector3(5, 5, 1), 2f);
//使物体大小从（5,5,1）变成自身大小
```

* 6.Punch：添加摇晃力（是从外部赋予的晃动）

```c#
 iTween.PunchPosition(this.gameObject, new Vector3(5, 5, 1), 2f);
 // 在物体坐标和目标位置晃动
iTween.PunchRotation(this.gameObject, new Vector3(0, 5, 0) * 90, 2f);
//让物体在Y轴方向旋转然后再转回来
iTween.PunchScale(this.gameObject, new Vector3(5, 5, 1), 2f);
//使物体先变大然后再变回来，有一个晃动的效果
RotateUpdate：跟RotateTo类似，该方法在Update中被调用，提供一个可改变属性值的环境。不用局限
于EaseType
```

* 7.Shake：摆动对象(从物体内部发出的力）

```c#
 iTween.ShakePosition(this.gameObject, new Vector3(5, 5, 1), 2f);
//物体在坐标内快速摆动（比晃动力摆动频率要快很多）
iTween.ShakeRotation(this.gameObject, new Vector3(0, 5, 0) * 90, 2f);
//物体在Y轴旋转来回摆动，幅度很大
 iTween.ShakeScale(this.gameObject, new Vector3(5, 5, 1), 2f);
//物体大小来回摆动
```

* 8.CameraFade：摄像机的淡入淡出

```c#
CameraFadeAdd:创建一个对象可以模拟摄相机的淡入淡出。

CameraFadeDepth：改变摄相机的淡入淡出深度(对象为CameraFadeAdd返回对象）

CameraFadeDestroy：删除摄相机的淡入淡出效果(对象为CameraFadeAdd返回对象）

CameraFadeSwap：改变摄相机的淡入淡出背景图(对象为CameraFadeAdd返回对象）

CameraFadeFrom:立即改变摄相淡入淡出的透明度然后随时间返回.amount:当执行淡入淡出时，其透明度的大小。（透明度越大，淡入淡出越快,个人认为100为满。此方法配合CameraFadeAdd使用，只有在CameraFadeAdd前提下，才可以进行淡入淡出操作。此方法为从CameraFadeAdd返回的对象出淡出到原来的界面。

CameraFadeTo：随时间改变摄相机淡入淡出透明度，（透明度越大，淡入淡出越快,个人认为100为满。此方法配合CameraFadeAdd使用，只有在CameraFadeAdd前提下，才可以进行淡入淡出操作。此方法为从本界面淡入到CameraFadeAdd返回的对象

CameraTexture：根据提供颜色创建一个full-screen Texture2D,可为CameraFade所用。（可在CameraFadeAdd方法中被调用）

```

两种音频方法


* 1.Audio：音量和音调的变化
```c#
AudioFrom:pitch和volum属性提供的是初始值
audioTo: pitch和volum属性提供的是终结值
audioUpdate:pitch和volum属性提供的是终结值 此方法用于Update()方法中
```
* 2.Stab ：播放AudioClip一次，不用手动加载AudioSource组件

一种颜色变换颜色
* 1.Color：变换颜色
```c#
ColorFrom:即刻改变对象的颜色值然后随着时间改变其回原来的颜色（总的来说，就是对GUIText和GUITexture的颜色的淡入淡出效果）。Color：此属性代表对象变化初始值。与audioFrom有异曲同工之效

ColorTo：随着时间改变对象的颜色组。同上例一样。Color：此属性代表对象变化最终值，与audioTo有异曲同工之效
```
一种值变化方法：

* 1，ValueTo：返回一个“from”和“to”之间的插值，用以改变属性每个方法一般有两种重载方式：最小定制选项、完全定制项。


Update类方法：提供每帧改变属性值的环境。在Update或FixedUpdate方法或类似于循环的环境中调用。
动画控制：Pause（暂停），Resume（恢复），Stop（停止并销毁iTween）

绘制方法：DrawLine(绘制线条)，DrawLineGizmos（绘制线条），DrawPath（绘制弯曲的路径）DrawPathGizmos（与DrawPath相同）

其他方法：Count（返回iTween的数量），PathLength（返回路径长度），PutOnPath（根据提供的百分比将物体放置于所提供路径上），PointOnPath（返回路径上指定百分比处的Vector3）

iTweenPath类：用于在Scene试图中编辑路径。

## 案例一

```c#
using UnityEngine;
using System.Collections;

public class Case1 : MonoBehaviour {

    public GameObject go;    //声明一个预设体
    public GameObject heart;  //声明准心
    RaycastHit hit = new RaycastHit();  //射线碰撞信息
    public Vector3[] paths = new Vector3[3];  //抛物线路径的坐标点的数组

	void Start () {
        paths[0] = new Vector3(0, 0, 0);  //小球的初始坐标不变，定义在Start中
	}
	void Update () {
        Heart(); 
        if(Input.GetMouseButton(0))
        {
            paths[2] = hit.point;   //抛物线终点是鼠标点击的位置
            paths[1] = new Vector3(hit.point.x /2, 4, hit.point.z/2);   //抛物线的最高点为点击位置的x，z，的一般，高度可以自己定义
            GameObject ball = Instantiate(go, new Vector3(0, 0, 0), Quaternion.identity) as GameObject;//在原点克隆一个预设体赋予ball（是为了让Destroy销毁对象）

            iTween.MoveTo(ball, iTween.Hash("path", paths, "time", 1f));    //让小球在该数组的路径下移动    
            Destroy(ball, 2);
        }
              
    }

    void Heart()
    {
        Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);  //发射一条射线

        if (Physics.Raycast(ray.origin, ray.direction, out hit, 100))
        {
            if (hit.collider.name == "Plane")
            {
                //Instantiate(go);
                //iTween.MoveUpdate(heart.gameObject, new Vector3(hit.point.x, hit.point.y + 0.5f, hit.point.z), 0.5f);
                heart.transform.position = new Vector3(hit.point.x, hit.point.y +0.2f, hit.point.z);  //准心的坐标为鼠标的位置（+0.2是防止准心与地板重合发生阴影）
            }
        }
    }

}
```

## 案例二

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/iTween%E7%BB%BC%E5%90%88%E6%A1%88%E4%BE%8B/images/Image.png)

```c#
using UnityEngine;
using System.Collections;
using UnityEngine.UI;

public class Ballbacks : MonoBehaviour {

    private Text text1;    
    Vector3 v;
    private Button btn;
	// Use this for initialization
    void Awake()
    {
        text1 = GameObject.Find("Canvas/Text").GetComponent<Text>();
        btn = GameObject.Find("Canvas/Button").GetComponent<Button>();
        btn.gameObject.SetActive(false);
        btn.onClick.AddListener(OnButton);
        v = this.gameObject.transform.position;

    }
	void Start () {
        iTween.MoveBy(this.gameObject, iTween.Hash("y", 4, "time", 2.5f, "easetype", iTween.EaseType.easeInOutExpo,
                                       "onstart", "showText", "onstarttarget", this.gameObject, "onstartparams", "上升开始..",
                                       "oncomplete", "showText", "oncompletetarget", this.gameObject, "oncompleteparams", "上升结束.."));

        iTween.RotateBy(this.gameObject, iTween.Hash("z", 0.25f, "time", 1f,"delay", 3.5f, "easetype", iTween.EaseType.easeInBack,
                                        "onstart", "showText", "onstarttarget", this.gameObject, "onstartparams", "旋转开始..",
                                       "oncomplete", "showText", "oncompletetarget", this.gameObject, "oncompleteparams", "旋转结束.."));
        iTween.MoveTo(this.gameObject, iTween.Hash("y",1f, "time", 2.5f, "delay", 5.5f, "easetype", iTween.EaseType.easeInQuart,
                                        "onstart", "showText", "onstarttarget", this.gameObject, "onstartparams", "下降开始..",
                                       "oncomplete", "showText", "oncompletetarget", this.gameObject, "oncompleteparams", "下降结束.."));
        iTween.ShakePosition(Camera.main.gameObject, iTween.Hash("amount", new Vector3(0.5f,0.5f,0), "time", 1f, "delay", 8.1f,
                                   "onstart", "showText", "onstarttarget", this.gameObject, "onstartparams", "震动开始..",
                                  "oncomplete", "ShowTextStop", "oncompletetarget", this.gameObject, "oncompleteparams", "所有运动结束.."));
	}
	
    void showText(string t)
    {
        text1.text += t + "\n";
    }
    void ShowTextStop(string t)
    {
        text1.text += t + "\n";
        btn.gameObject.SetActive(true);
    }

    public void OnButton()
    {
        this.gameObject.transform.position = v;
        this.gameObject.transform.rotation = Quaternion.identity;
        text1.text = "";
        btn.gameObject.SetActive(false);

        Start();
    }	
}
```

## 案例三

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/iTween%E7%BB%BC%E5%90%88%E6%A1%88%E4%BE%8B/images/Image3.png)

代码如下：

#### 小方块变颜色控制

```c#

public class ChangeColor : MonoBehaviour {
    //记录开始时的颜色
    public Color StartColor;
    //监测物体是否被点击过
    bool isActive;
    private void Start()
    {
        StartColor = this.gameObject.GetComponent<MeshRenderer>().material.color;
    }

    private void OnMouseEnter()
    {
        if (!isActive)  //地板没有被点击的时候
       {
            if(!CreateFloor.isBallmove)   //当小球没有运动的时候
           {
                iTween.ColorTo(this.gameObject, Color.green, 0.1f);
                iTween.MoveTo(this.gameObject, iTween.Hash("y", 0.4f, "time", 0.1f));
            }
            else
            {
                iTween.ColorTo(this.gameObject, Color.yellow, 0.1f);
                iTween.MoveTo(this.gameObject, iTween.Hash("y", 0.4f, "time", 0.1f));
            }
        }
    }
    private void OnMouseExit()
    {
        if(!isActive)       //鼠标退出方块时，没有被点击过的颜色才变回原来颜色 
        {
            iTween.ColorTo(this.gameObject, StartColor, 0.1f);
            iTween.MoveTo(this.gameObject, iTween.Hash("y", 0, "time", 0.1f));
        }
       
    }
    private void OnMouseDown()
    {
        if(!CreateFloor.isBallmove)   //当小球没有运动的时候地板才能被点击
        {
            isActive = true;
            iTween.ColorTo(this.gameObject, Color.red, 0.1f);
            iTween.MoveTo(this.gameObject, iTween.Hash("y", 0, "time", 0.1f));
            SendMessageUpwards("BallMoveTarget", this.gameObject);  //向父级发送消息
        }
      
    }
    void Deactivate()
    {
        isActive = false;
        iTween.ColorTo(this.gameObject, StartColor, .4f);
    }

}
```
#### 创建地板和控制球移动

```c#
public class CreateFloor : MonoBehaviour {

    public GameObject floor;
    public int row = 9;   //创建地板的行数
    public int lie = 9;   //创建地板的列数

    public GameObject ball;
    private void Awake()
    {
        floor = Resources.Load("floor")as GameObject;      
    }
    void Start () {
        //克隆小球生成到地板中央位置
        ball = GameObject.Instantiate(Resources.Load("Sphere"),new Vector3(row/2,0.7f,lie/2), Quaternion.identity) as GameObject;

        for (int i = 0; i < row; i++)
        {
            for (int j = 0; j < lie; j++)
            {
                GameObject clone = GameObject.Instantiate(floor, new Vector3(j, 0, i), Quaternion.identity)as GameObject;
                clone.transform.SetParent(Camera.main.transform);
                if ((i + j) % 2 == 0)
                {
                    //偶数位置的物体变黑色
                    clone.GetComponent<MeshRenderer>().material.color = Color.black;
                }
            }
        }
	}
    GameObject currentTarget;
    public static bool isBallmove = false;  // 标记求是否是运动状态
    public void BallMoveTarget(GameObject target)   //传进来被点击的地板
    {
        if (currentTarget != null && target != currentTarget)   //小球所在的地板被点击，下一次点击的不是小球所在地板                       
        {
            currentTarget.SendMessage("Deactivate");    //发送消息，让小球可以移动
       }
        currentTarget = target;
        isBallmove = true;
        float moveTime = Vector3.Distance(ball.transform.position, target.transform.position) / 10;  //通过距离换算时间
        iTween.MoveBy(ball, iTween.Hash("x", (target.transform.position.x - ball.transform.position.x), "time",                                                                                               moveTime,"easetype",iTween.EaseType.linear)); //移动小球X轴
        iTween.MoveBy(ball, iTween.Hash("z", (target.transform.position.z - ball.transform.position.z), "time", moveTime, "delay",                          moveTime, "easetype", iTween.EaseType.linear,"oncomplete","Reset","oncompletetarget",this.gameObject));//移动小球Z轴
    }
    private void Reset()   //小球移动完成调用该方法
    {
        isBallmove = false;
    }
}
```
