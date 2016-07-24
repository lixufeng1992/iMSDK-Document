## 4.4.7 游戏服务(Game)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMGame |该模块主要是提供游戏服务，如成就、排行榜等|

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMGame（GameObject）上，开发者不要主动销毁该对象！</font>


### 快速入门

1. [完成特定渠道配置](../../Channel/README.md)
2. 代码实现

```cs
void Start() {
 // 我们建议在游戏开始时就初始化登陆方法
 IMSDKApi.Login.Initialize ();
}

// 解锁成就

```

### 工程配置说明

#### Android工程配置说明

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

#### iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。
    
### 参考

* 游戏服务方法类 <font color=blue>IMGame</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数 |
| public bool SetChannel(string channel) | 设定游戏服务渠道 |
| public void Setup(GameCallback callback=null) | 初始化环境 |
| public void CheckGMSInstall(GameCallback callback) | 【Android】检查Google服务是否安装 |
| public bool Available() | 【Android】服务是否可用 |
| public void UnlockAchieve(string achieve, GameCallback callback =null) | 解锁单步成就 |
| public void UnlockAchieve(string achieve, int count, GameCallback callback =null) | 【Android】解锁多步成就 |
| public void UnlockAchieve(string achieve, double percent, GameCallback callback =null) | 【iOS】按百分比解锁成就 |
| public void ShowAchieves() | 显示成就 |
| public void ShowAchieves(GameCallback callback) | 【Android】显示成就 |
| public void SetScore(string board, int score,GameCallback callback = null) | 设定排行榜分数 |
| public void ShowLeaderBoard(string board) | 显示排行榜 | 
| public void ShowLeaderBoard(string board, GameCallback callback) | 【Android】显示排行榜 |




