# Uniyt3D-

## 什么是unityAds

是Unity官方的的一个广告平台，是Unity云服务的一部分，接入简单API提供的比较好

### 其他广告平台

有米，芒果移动广告，广点通，百灵欧拓等

## 添加UnityAds步骤

1.下载广告插件并导入到unity中 http://www.assetstore.unity3d.com/en/#!/content/21027
2.注册登录账号http://unityads.unity3d.com
3.添加游戏，并获取游戏ID（GameID）
4.在脚本中引入命名空间using UnityEngine.Advertisements；
5.初始化广告Advertisement.Initialize("<YOUR GAME ID HERE>")
6.展示广告 if（Advertisement.isReady()）{Advertisement.Show();}

## unityAds官网

https://dashboard.unityads.unity3d.com/
