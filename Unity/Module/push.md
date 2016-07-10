## 4.4.5 推送模块(Push)

### 基础信息

|命名空间|调用用入口|模块说明|
|:--|:--|:--|
|Tencent.iMSDK|IMSDKApi.Push|该类自动绑定在Unity的Tencent.iMSDK.IMPush（GameObject）上<br> 开发者不要主动销毁该对象|

### 快速入门

1. #### [选择渠道，完成配置](../../Channel/README.md)
2. #### 代码实例，下面的代码块是最基本调用代码

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

### 参考

* 
推送方法类 <font color=blue>IMPush</font>

| 函数名 | 函数说明 |
| -- | -- |
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



