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



