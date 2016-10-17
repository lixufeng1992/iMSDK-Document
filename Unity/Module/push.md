## 4.4.5 推送模块(Push)

### 基础信息

|命名空间|调用用入口|模块说明|
|:--|:--|:--|
|Tencent.iMSDK|IMSDKApi.Push|该类自动绑定在Unity的Tencent.iMSDK.IMPush（GameObject）上<br> 开发者不要主动销毁该对象|

### 快速入门

1.  [选择渠道，完成配置](../../Channel/README.md)
2.  代码实例，下面的代码块是最基本调用代码

```
void Start() {
    //初始化
    IMSDKApi.Push.Initialize ();
    //设置需要使用推送渠道，比如“XG”就是使用信鸽推送
    IMSDKApi.Push.SetChannel("XG");
    //进行注册，控制台看到“注册成功”，就可以接收到后台消息推送
    IMSDKApi.Push.Register();
}
```

### 特别说明

|版本信息|版本说明|备注|
|:--|:--|:--|
|(1)Xg_sdk_vgcm_vip_1.0_20161009_2020.jar <br>  (2) Xg4GCM-vgcm_vip_1.0_20161009_2020.jar| 可以通过配置开启合并UI或者独立通知|只通过GCM推送消息|
|(1)Xg_sdk_vgcm_vip_inbox_1.0_20161009_2019.jar <br> (2) Xg4GCM-vgcm_vip_inbox_1.0_20161009_2019.jar|只有独立通知|只通过GCM推送消息，<br>上Google推荐位要求去掉的独立通知代码|

### 参考

* 
推送方法类 <font color=blue>IMPush</font>

| 函数名 | 函数说明 |
| :-- | :-- |
| public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 |
| public bool SetChannel(string channel) | 设置推送渠道，如：XG（信鸽） |
| public string GetChannel() | 获取当前设定渠道 |
| public void Register(string account = "") | 注册 |
| public void SetRegisterCallback(PushCallback callback) | 设定注册回调函数 |
| public void Unregister() | 反注册 |
| public void SetUnregisterCallback(PushCallback callback) | 反注册回调 |
| public void SetTag(string tag) | 设定用户标签 |
| public void SetTag(List< string > tags) | 设定多个用户标签 |
| public void SetTagCallback(PushCallback callback) | 设定用户标签回调 |
| public void DelTag(string tag) | 删除标签 |
| public void DelTag(List< string > tags) | 删除多个标签 |
| public void SetDelTagCallback(PushCallback callback) | 设定删除标签回调 |
| public void SetNotifyRecvCallback(PushNotifyCallback callback) | 设定接收推送消息回调 |
| public void SetNotifyClickCallback(PushNotifyCallback callback) | 设定点击推送消息回调 |
| public void SetNotifyShowCallback(PushNotifyCallback callback) | 设定推送消息显示回调 |     
| public void AddLocalNotification(IMLocalMessage message, Dictionary<string, string> userinfo = null) |本地推送，Android不支持扩展userinfo|
| public void ClearLocalNotifications() |清空本地通知|
| public void DeleteLocalNotifications(string key) |IOS特有，删除特定的本地通知|

* 本地消息体 <font color=blue>IMLocalMessage</font>

| 类型 | 说明 | 备注 |
| :--------------------------- | :---------------------------------------- | :------------------------- |
| public string Content | 消息内容 | Android，IOS共用，必须填 |
| public long FireTime | 弹出消息Unix时间戳 | Android，IOS共用，必须填 |
| public string Title | 消息标题 | Android，必须填 |
| public int Type | 消息类型，默认是1. （1:通知，0:消息） | Android，选填 |
| public int ActionType | 通知动作类型，默认是1。<br>  1: 打开activity或app本身 <br>  2: 打开浏览器 <br>  3: 打开Intent <br>  4: 通过包名打开应用   | Android，选填 |
| public string ActionContent | 对应动作类型的具体内容，<br>比如ActionType为1是，这个可以填Activity将要打开的Activity的字符串，如果不填默认是本省 | Android，选填，配合ActionType使用 |
| public bool IsRinging | 通知来的时候是否响铃，默认是响铃 | Android，选填 |
| public string RingRaw | 可以配置响铃的铃声地址 | Android，选填 |
| public bool IsVibrate | 通知来的时候是否震动，默认是震动 | Android，选填 |
| public int Light | 打开呼吸灯，默认1 是打开（1:打开，0:关闭） | Android，选填 |
| public string IconRes | 设置应用内图标文件名（xg.png）或者下载图标的url地址,例如:xg或者图片url | Android，选填 |
| public int BuilderId | 设置消息样式，默认为0或不设置。详见自定义本地通知样式章节说明 | Android，选填 |
| public int StyleId | 设置Web端设置是否覆盖编号build_id的通知样式，默认1，0否，1是 | Android，选填 |

### 代码示例
1. 使用opendId进行注册，这样可以对单个openId进行推送

 ```
 void Start() {
     //初始化
     IMSDKApi.Push.Initialize ();
     //设置需要使用推送渠道，比如“XG”就是使用信鸽推送
     IMSDKApi.Push.SetChannel("XG");
     //监听注册，可以获取是否注册成功的消息
     IMSDKApi.Push.SetRegisterCallback(PushCallback callback);
     //进行注册
     IMSDKApi.Push.Register("openId");
 }
 ```

2. 7天内未登录的用户，进行推送，需要用户自己的服务器后台配合

 ```
 void Start() {
     //初始化 
 	 IMSDKApi.Push.Initialize ();
     //设置需要使用推送渠道，比如“XG”就是使用信鸽推送
	 IMSDKApi.Push.SetChannel("XG");
     //监听注册，可以获取是否注册成功的消息
     IMSDKApi.Push.SetRegisterCallback(PushCallback callback);
     //进行注册
	 IMSDKApi.Push.Register("openId");
     //获取当前时间保存在本地，并且上报给服务器。
     //这样后台就清楚哪些客户在那一天登录，就可以筛选出7天未登录的用户
     IMSDKApi.Push.SetTag("本次登录时间");
     //获取保存在本地的上一次登录时间
     IMSDKApi.Push.DelTag("上一次登录时间");
 }
 ``` 

3. 增加本地推送

```
     DateTime Jan1st1970 = new DateTime (1970, 1, 1, 0, 0, 0, DateTimeKind.Utc);         
     IMLocalMessage message = new IMLocalMessage (); 
     message.Title = "Local Notification"; 
     message.Content = "Local Notification Content"; 
     message.FireTime = 5 * 1000 +  + (long) (DateTime.UtcNow - Jan1st1970).TotalMilliseconds;// 5秒后弹出通知
     IMSDKApi.Push.AddLocalNotification (message); 
``` 
 
### <font color=red> iOS推送注意事项 </font>   
+ 需要在App生命周期内进行如下调用   

```
- (void)application:(UIApplication *)application
    didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken {
  [[IMSDKApplicationDelegate sharedInstance] application:application didRegisterForRemoteNotificationsWithDeviceToken:deviceToken];
}

// 如果deviceToken获取不到会进入此事件
- (void)application:(UIApplication *)application
    didFailToRegisterForRemoteNotificationsWithError:(NSError *)error {
  [[IMSDKApplicationDelegate sharedInstance] application:application
        didFailToRegisterForRemoteNotificationsWithError:error];
}

- (void)application:(UIApplication *)application
    didReceiveRemoteNotification:(NSDictionary *)userInfo {
  [[IMSDKApplicationDelegate sharedInstance] application:application
                            didReceiveRemoteNotification:userInfo];
}

```

