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
bool isSetup = false;

// 初始化环境回调，会拉起GooglePlay、GameCenter登录
void OnSetup(IMResult result) {
    if（result.RetCode == 1）{
        isSetup = true;
    }
}

// Android : 当显示GooglePlay和GameCenter成就或排行榜界面出错时，建议重启游戏
void OnShowUI(IMResult result) {
    if(result.RetCode != 1) {
        // 当界面显示出错时，需要重新加载游戏或退出
        Application.Quit();
    }
}

void Start() {
 // 我们建议在游戏开始时就初始化登陆方法
 IMSDKApi.Game.Initialize ();
 // 调用
 IMSDKApi.Game.Setup();
}

// 解锁成就
if(isSetup) {
    IMSDKApi.Game.UnlockAchieve("CgkIkcSMwNYHEAIQAQ");
}

// 显示成就
if(isSetup) {
    IMSDKApi.Game.ShowAchieves();
}

// 上报分数（用于排行榜）
if(isSetup) {
    IMSDKApi.Game.SetScore("CgkIkcSMwNYHEAIQAw", 10000);
}

// 显示排行
if(isSetup) {
    IMSDKApi.Game.ShowLeaderBoard();
}

```

### 【重要】问题说明

* 渠道说明

    目前，iMSDK只支持GooglePlay和GameCenter的两个游戏服务，暂时不需要设置渠道

* 初始化说明
    
    必须先调用Setup成功之后，才能调用相关的上报函数，可参看快速入门示例代码

* GooglePlay 登出问题

    GooglePlay显示成就和排行榜界面的界面时，需要重新调用登录逻辑重新进入游戏，有可能用户在UI界面中替换了用户或者登出

    
### 参考

* 游戏服务方法类 <font color=blue>IMGame</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数 |
| public bool SetChannel(string channel) | 设定游戏服务渠道，GooglePlay或GameCenter可以不用调用 |
| public void Setup(GameCallback callback=null) | 初始化环境，必须成功后再调用其他函数 |
| public void SignOut(GameCallback callback=null) | 【Android】退出登录，须重新调用Setup后才能是用其他功能 |
| public void CheckGMSInstall(GameCallback callback) | 【Android】检查Google服务是否安装 |
| public bool Available() | 【Android】检查Google服务是否可用 |
| public void UnlockAchieve(string achieve, GameCallback callback =null) | 解锁单步成就，achieve为成就ID |
| public void UnlockAchieve(string achieve, int count, GameCallback callback =null) | 【Android】解锁多步成就，achieve为成就ID |
| public void UnlockAchieve(string achieve, double percent, GameCallback callback =null) | 【iOS】按百分比解锁成就，achieve为成就ID |
| public void ShowAchieves() | 显示成就 |
| public void ShowAchieves(GameCallback callback) | 【Android】显示成就，并提供回调 |
| public void SetScore(string board, int score, GameCallback callback = null) | 设定排行榜分数, board为排行榜ID |
| public void ShowLeaderBoard(string board) | 显示排行榜，board为排行榜ID | 
| public void ShowLeaderBoard(string board, GameCallback callback) | 【Android】显示排行榜，board为排行榜ID |




