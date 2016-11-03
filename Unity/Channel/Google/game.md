## Google Play游戏服务模块

### 支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool SetChannel(string channel) | 设定渠道 | √ | - |
| 3 | public void Setup(GameCallback callback=null) | 初始化环境 | √ | - |
| 4 | public void CheckGMSInstall(GameCallback callback) | 【Android】检查Google服务是否安装 | √ | - |
| 5 | public bool Available() | 【Android】服务是否可用 | √ | - |
| 6 | public void UnlockAchieve(string achieve, GameCallback callback =null) | 解锁单步成就 | √ | - |
| 7 | public void UnlockAchieve(string achieve, int count, GameCallback callback =null) | 【Android】解锁多步成就 | √ | - |
| 8 | public void UnlockAchieve(string achieve, double percent, GameCallback callback =null) | 【iOS】按百分比解锁成就 | √ | - |
| 9 | public void ShowAchieves() | 显示成就 | √ | - |
| 10 | public void ShowAchieves(GameCallback callback) | 【Android】显示成就 | √ | - |
| 11 | public void SetScore(string board, int score,GameCallback callback = null) | 设定排行榜分数 | √ | - |
| 12 | public void ShowLeaderBoard(string board) | 显示排行榜 | √ | - |
| 13 | public void ShowLeaderBoard(string board, GameCallback callback) | 【Android】显示排行榜 | √ | - |


### Google登录说明

一般情况下，只有使用先登录（连接）到Google Play服务

```cs
bool connected = false;

void Start() {
  IMSDKApi.GameService.Initialize();
  IMSDKApi.GameService.SetChannel("GooglePlay");
  IMSDKApi.GameService.Setup(OnSetup);
}

void OnSetup(IMResult setupResult) {
  if(setupResult.RetCode == 1) {
    connected = true;
  }
  else {
    ...
  }
}

void AchieveSomething() {
  if(connected) {
    IMSDKApi.GameService.UnlockAchieve("some_achieve");
  }
}
```

如果登录模块使用了GooglePlay，那么无需调用Setup也可以上报成就

### 上报成就账号说明

上报成就的账号是连接GooglePlay服务的账号，我们并不提供自动与当前登录账号绑定，可以通过如下例子说明：

1. 用户用Faceboook账号FB-A登录
2. 连接到手机GooglePlay账号GP-A
3. 用户登录后完成成就，这个时候是上报到GP-A账号上的成就

由于这两个账号没有关联关系，所以当切换账号的时候，成就不能随之切换，如：

* 用户切换到FB-B账号登录，游戏进度被重置，GooglePlay服务还是使用GP-A，那这个时候GP-A账号的成就依然存在
* 用户切使用GP-B账号登录，游戏进度保持不变，GooglePlay服务使用新账号GP-B，这个时候，GP-B账号成就为空

所以，在使用非GooglePlay登录的时候依然使用GooglePlay游戏服务，逻辑上是有问题的

### 工程配置

#### Android工程配置

* 完成[通用配置](../../../Channel/Google/android.md)
  
  配置网络权限和GMS版本配置
  
* 添加配置

  ```xml
  <meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ 263738040849" />
  ```
  
  注意：value需要修改为游戏对应的值