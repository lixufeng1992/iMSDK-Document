## 4.4.6 统计模块(Stat)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Stat |用于上报统计数据|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMStat（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门
1. [完成特定渠道配置](../../Channel/README.md)
2. 代码实例

```json
//stat.json 文件格式示例
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
### 代码示例

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

其中：
* eventReport 为事件上报渠道列表
* eventTrack 为事件跟踪渠道列表
* pageTrack 为页面跟踪渠道列表
* purchaseReport 为支付上报渠道列表
* testSpeed 为网速统计渠道列表
* exceptionReport 为异常上报渠道列表
* crashReport 为崩溃上报渠道列表


### 参考
* 统计方法类IMStat

支持功能列表

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

### 工程配置说明

#### Android工程配置说明

##### 初始化配置

如果采用配置文件的形式进行初始化，需要将配置文件放到Unity工程

```sh
Assets/Plugins/Android/asssets/IMSDK/stat.json
```

文件中即可

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

#### iOS工程配置说明

##### 初始化配置

如果采用配置文件的形式进行初始化，需要将配置文件放到iOS工程

```sh
Data/Raw/IMSDK/stat.json
```

文件中即可

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。



