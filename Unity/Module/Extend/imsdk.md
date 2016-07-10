## 4.4.13.1 iMSDK功能扩展(Tool)


### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMTool |iMSDK 的扩展工具|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMLogin（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门

1. 代码实例

```cs
	private IMToolDeviceInfo deviceInfoObj;
	private string deviceInfoStr;
    private string public string packageChannelId;
    
    
    deviceInfoObj = IMSDKApi.Tool.GetInfoObj();
    deviceInfoStr = IMSDKApi.Tool.GetInfoStr();
    packageChannelId = deviceInfoObj.PackageChannelId;
    //或者
    //packageChannelId = IMSDKApi.Tool.GetPackageChannelId();

```

### 参考

* GetInfoObj返回结构体 <font color=blue>IMToolDeviceInfo </font>

| 变量 | 说明 |
| :-- | :-- |
| public string PackageChannelId  | 打包渠道ID |
| public string GuestId | 用户GuestID |
| public string AppVersionName | app的versionName |
| public int AppVersionCode | app的versionCode |
| public string OSName | 设备的系统名称 |
| public string OSVersion | 设备系统版本号 | 
| public int Width | 设备宽 |
| public int Height | 设备高 |
| public string Network | 获取设备网络类型，如"tencent-staffwifi" |
| public string IMEI | 设备imei号 |
| public string Operators | 设备运营商 |
| public string Apn | 设备网络apn，如"wap", "net"等 |
| public string Brand | 设备brand |
| public string Manufacturer | 设备制造商 |
| public string Model | 设备model |
| public string PhoneName | 设备名称 |
| public string Language | 设备语言 |
| public string Country | 设备所在国家 |
| public string AndroidId | 设备AndroidId |
| public string Mac |设备mac地址 |
| public string SeriesId | 设备SeriesId |

* 接口说明

| 函数名 | 函数说明 |
| :-- | :-- |
| GetInfoStr() | 获取所有信息，包括如下这些信息(返回 json 字符串) |
| GetInfoObj() | 获取所有信息，包括如下信息(返回 IMToolDeviceInfo ) | 
| GetPackageChannelId() | 获取渠道包apk的packageChannelId |
| GetGuestId() | 获取用户guestId，guestId为用户imsdk用户游客id |
| GetAppVersionName() | 获取应用的versionName |
| GetAppVersionCode() | 获取应用的versionCode |
| GetOSName() | 获取用户操作系统类型，Android用户为"Android" |
| GetOSVersion() | 获取用户操作系统版本，如4.4.4 |
| GetWidth() | 获取设备屏幕宽度 |
| GetHeight() | 获取设备屏幕高度 |
| GetNetwork() | 获取设备网络类型，如"tencent-staffwifi" |
| GetIMEI() | 获取设备imei号 |
| GetOperators() | 获取设备运营商 |
| GetApn() | 获取设备网络apn，如"wap", "net"等 |
| GetBrand() | 获取设备brand |
| GetManufacturer() | 获取设备制造商 |
| GetModel() | 获取设备model |
| GetPhoneName() | 获取设备名称 | 
| GetLanguage():获取设备语言 |
| GetCountry() | 获取设备所在国家 |
| GetAndroidId() | 获取设备AndroidId |
| GetMac() | 获取设备mac地址 |
| GetSeriesId() | 获取设备SeriesId |

### 代码示例


* 


// 调用登录
IMSDKApi.Login.Login(OnLogin);

```

* #### 多登陆态共存说明

iMSDK支持多登陆态共存，如:

```cs
// Facebook 登陆
IMSDKApi.Login.SetChannel("Facebook");
IMSDKApi.Login.Login();

// WeChat 登陆
IMSDKApi.Login.SetChannel("WeChat");
IMSDKApi.Login.Login();
```
    
如果两次登陆都成功的话，那么本地会有两个有效的登录态，可以通过SetChannel方法进行切换。

```cs
// 获取 Facebook 登陆数据
IMSDKApi.Login.SetChannel("Facebook");
IMLoginResult facebookLoginResult = IMSDKApi.Login.GetLoginResult();

// 获取 WeChat 登陆数据
IMSDKApi.Login.SetChannel("WeChat");
IMLoginResult wechatLoginResult = IMSDKApi.Login.GetLoginResult();
```

同样，登出时也需要根据渠道进行登出。

```cs
// 登出Facebook
IMSDKApi.Login.SetChannel("Facebook");
IMSDKApi.Login.Logout();

// 登出微信
IMSDKApi.Login.SetChannel("WeChat");
IMSDKApi.Login.Logout();
```

* #### 绑定功能说明

iMSDK提供了一套账号绑定机制，可以实现不同渠道的账号关联。

绑定另外一个渠道之前，必须先登录一个渠道

```cs
// 先登录到游客
IMSDKApk.Login.SetChannel("Guest");
IMSDKApi.Login.Login();

// 绑定到Facebook
IMSDKApi.Login.Bind("Facebook");
```

<font color=red> 注意：</font>

1. 绑定之后，需要特别留意回调返回值，OpenID不变，但Token会发生变化，需要注意刷新游戏服务器后台的Token，避免出现后台Token失效的情况 ！
2. 绑定返回数据可以能是原渠道数据，也有可能是目标渠道数据，可根据游戏需要进行配置，这一点需要特别小心！


* #### 本地登录态失效说明

<font color=orange>登录数据是有有效期的，游戏后台需要判断iMSDK的登录态</font>

QuickLogin及GetLoginResult是根据本地保存数据进行判断的，可能出现登录态失效的情况，所以，游戏服务器后台必须与iMSDK后台校验登录态。

示例伪代码：

```cs
// 游戏启动时初始化
IMSDKApi.Login.Initialize();

...

// 快速登录回调处理
void OnQuickLogin(IMLoginResult result) {
    // 快速登录成功
    if(result.RetCode == 1) {
        // 连接到服务器
        int ret = ConnectToGameServer(result.OpenId, result.GuidToken, ...);
        // 如果服务器返回校验登录态失败
        if(ret == RET_SERVER_LOGIN_DATA_EXPIRED) {
            //登出清理本地数据
            IMSDKApi.Login.Logout();
            //提示用户
            if(ConfirmToCallLogin()) {
                IMSDKApi.Login.Login(OnLogin);
            }
            else{
                ...
            }
        }
    }
    // 快速登录失败
    else {
        ...
    }
}

...

// 设定渠道获取登录数据
IMSDKApi.Login.SetChannel("Facebook");
// 使用快速登录
IMSDKApi.Login.QuckLogin(OnQuickLogin);
...
```

* #### 子渠道登录说明

部分渠道集成了许多子渠道，在调用登录组件时，需要指定子渠道，iMSDK 侧通过调用设定子渠道来调用相应的登录功能

```cs
IMSDKApi.Login.SetChannel("Garena");
IMSDKApi.Login.SetLoginType("GRN_FB");
IMSDKApi.Login.Login(OnGarenaFacebookLogin);
```

子渠道可以在“渠道使用说明”章节中找到

* #### 严格登录说明

严格登录(StrictLogin)是指，只有注册或者绑定用户才能登录成功，该功能可以实现登录是依附于一个基础账号的需求。

```cs
IMSDKApi.Login.StrictLogin(OnStrictLogin);
```

应用场景如下：
1. 游戏进入时没有登录界面，直接用一个渠道登录，如游客（Guest）
2. 在游戏中，提供一个绑定界面，可以绑定到其他社交渠道
3. 绑定完成后，可以用StrictLogin进行登录
4. 如果社交渠道尚未注册，调用该方法会返回失败


* #### 上报状态功能说明

部分渠道支持状态上报功能（类似QQ在线状态），可以通过上报修改玩家的状态

调用逻辑：
1. 设定上报渠道

  ```cs
  IMSDKApi.Login.SetPlayingReportChannel(CHANNEL);
  ```

2. 上报状态，如“正在玩游戏”

  ```cs
  IMSDKApi.Login.ActivatePlayingReport();
  ```
  
3. 游戏退出或类似状态，取消上报

  ```cs
  IMSDKApi.Login.DeactivatePlayingReport();
  ```
  

  
* #### 渠道安装判断说明

目前，只有极少的几个渠道提供了判断渠道是否安装的方法（如微信），使用该接口是需要小心

1. 判断渠道是否安装
  
  ```cs
  if(IMSDKApi.Login.IsChannelSupportApi()) {
    //TODO
    Debug.Log("application api level supported");
  }
  ```
  
2. 判断渠道Api是否支持

  ```cs
  if(IMSDKApi.Login.IsChannelAppInstalled()) {
    //TODO
    Debug.Log("application is installed");
  }
  ```



