## 4.4.6 统计模块(Stat)

 # 数据上报模块(Stat)

## 命名空间

```cs
Tencent.iMSDK
```

## 接口类

```cs
    IMSDKApi.Stat
```

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMStat（GameObject）上，开发者不要主动销毁该对象！</font>


## 模块使用说明

### 支持功能列表

| 功能 | 函数名 | 备注 |
| :--: | ----- | :--: |
| 事件上报 | ReportEvent | - |
| 事件跟踪 | TrackEventBegin、TrackEventEnd | 两个函数成对出现 |
| 跟踪页面 | TrackPageBegin、TrackPageEnd | 两个函数成对出现 |
| 支付上报 | ReportPurchase | - |
| 网速统计 | SpeedTest | - |
| 开启异常上报 | SetAutoExceptionReport | - |
| 开启崩溃上报 | SetAutoCrashReport | - |


### 初始化方式

一个App可以使用多个统计渠道，为了简化初始化过程，iMSDK提供了两种初始化模式：

* 配置文件
  
  在代码层，需要先调用如下初始化函数
  
  ```cs
  public bool Initialzie()
  ```
  
  通过配置文件，可以方便的修改上报渠道，无需修改代码，文件内容可以参考如下的JSON格式
  
  ```json
  {
    "eventReport":["MTA","Adjust"],
    "eventTrack":["MTA"],
    "purchaseReport":["Adjust","Facebook"],
    "exceptionReport":["Bugly"],
    "crashReport":["Bugly"],
    "pageTrack":["MTA"],
    "testSpeed":["MTA"]
  }
  ```
  
  其中：
  
    * eventReport 为事件上报渠道列表
    * eventTrack 为事件跟踪渠道列表
    * pageTrack 为页面跟踪渠道列表
    * purchaseReport 为支付上报渠道列表
    * testSpeed 为网速统计渠道列表
    * exceptionReport 为异常上报渠道列表
    * crashReport 为崩溃上报渠道列表
    
  将文件放到指定位置，就可以初始化对应的渠道

* 接口调用

  通过下面的函数调用在代码中指定相应的渠道类别
  
  ```cs
  public bool Initialize(IMStatChannelLists channelLists) 
  ```

### 初始化说明

在调用初始化函数时，需要尽早调用，并在登录完成后，再次调用初始化

我们建议尽早调用初始化接口代码，如在程序启动的后初始化接口

```cs
// 我们建议在首个场景调用初始化代码，并设定异常上报

void InitializeStat() {
  IMStatChannelLists channelLists = new IMStatChannelLists();
  channelLists.EventReportChannels.Add("Facebook");
  ...
  IMSDKApi.Stat.Initialize (channelLists);
  IMSDKApi.Stat.SetAutoExceptionReport(true);
  IMSDKApi.Stat.SetAutoCrashReport(true);
}

void Start() {
  ...
  InitializeStat();
  ...
}

```

这时候，上报信息是没有用户资料（openid等）的，所以需要在登录后，再次调用初始化

```cs
void OnLogin() 
  ...
  InitializeStat();
  ...
}
...
IMSDKApi.Login.Login();
```

### 实时上报说明

在接口中，我们提供的一个实时上报标记为，但是这个标记位也需要根据上报的平台进行判断，如果平台本身不支持，那iMSDK也无法进行实时上报

### 过滤上报渠道

默认情况下，在初始化的所有渠道我们都会进行上报，但是想要部分数据只上报到指定的渠道，就可以通过过滤器来实现

譬如说，支付数据比较敏感，如果只需要上报到腾讯的MTA，则可以采用下面的方式进行代码调用

```cs
List<string> filters = new List<string>();
filters.Add("MTA");
IMSDKApi.Stat.SetFilter(filters);
IMSDKApi.Stat.ReportPurchase("buy_some_thing", "CNY", "99.99", true);
IMSDKApi.Stat.ClearFilter();
```

当然也可以根据业务需求封装成函数，简化调用

### 异常及崩溃上报功能说明

目前，我们只提供Android、iOS平台Native层的Crash上报，Unity部分并不支持。

Bulgy平台提供的Unity的插件，可以到Bugly官网下载：[http://bugly.qq.com/whitebook](http://bugly.qq.com/whitebook)

## 工程配置说明

### Android工程配置说明

#### 初始化配置

如果采用配置文件的形式进行初始化，需要将配置文件放到Unity工程

```sh
Assets/Plugins/Android/asssets/IMSDK/stat.json
```

文件中即可

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

### iOS工程配置说明

#### 初始化配置

如果采用配置文件的形式进行初始化，需要将配置文件放到iOS工程

```sh
Data/Raw/IMSDK/stat.json
```

文件中即可

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。


## 参考

* 渠道初始化列表构体 <font color=blue>IMStatChannelLists</font>

| 变量 | 说明 |
| -- | -- |
| public List<string> EventReportChannels | 事件上报渠道列表 |
| public List<string> EventTrackChannels | 事件跟踪渠道列表 |
| public List<string> PageTrackChannels | 页面跟踪渠道列表 |
| public List<string> TestSpeedChannels | 网络统计渠道列表 |
| public List<string> ExceptionReportChannels | 异常上报渠道列表 |
| public List<string> CrashReportChannels | 崩溃上报渠道列表 |


* 数据上报方法类 <font color=blue>IMStat</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，并且须配置渠道列表，在调用其他函数之前需要调用该函数 |
| public bool Initialize(IMStatChannelLists channelLists) | 指定渠道的初始化方法，在调用其他函数之前需要调用该函数 |
| public void ReportEvent(string eventName, bool realtime = false) | 上报事件 |
| public void ReportEvent(string eventName, string eventBody, bool realtime = false) | 上报事件，并设定事件体 |
| public void ReportEvent(string eventName,  Dictionary< string, string> paramDict, bool realtime = false) | 上报事件，并设定事件体 |
| public void ReportPurchase(string purchaseName, string currencyCode, string expense, bool realtime = false) | 上报支付事件 |
| public void TrackEventBegin(string eventName, string eventBody) | 事件跟踪开始 |
| public void TrackEventEnd(string eventName, string eventBody) | 事件跟踪结束 |
| public void TrackPageBegin(string pageName) | 页面跟踪开始 |
| public void TrackPageEnd(string pageName) | 页面跟踪结束 |
| public void SpeedTest(List< string > hostList) | 网络测试 |
| public void SpeedTest(Dictionary< string, int > hostDict) | 带端口的网络测试 |
| public void SetAutoExceptionReport(bool enable = false) | 设定异常自动上报开关 |
| public void SetAutoCrashReport(bool enable = false) | 设定异常退出上报开关 |

## 代码示例

```cs
void Start() {
    IMStatChannelLists channelLists = new IMStatChannelLists();
    
    channelLists.EventReportChannels.Add("Facebook");
    ...
    
    IMSDKApi.Stat.Initialize (channelLists);
}

IMSDKApi.Stat.ReportEvent("start");

```

void TestSendMessage() {
    IMFriendContent content = new IMFriendContent();

    content.Type = IMFriendContent.MessageType.LINK_DIALOG;
    content.Title = "this is title";
    content.Content = "this is content";
    content.Link = "http://ieg.qq.com";
    content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
    content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";

    IMSDKApi.Friend.SendMessage(content, TestFriendCallback);
}

```