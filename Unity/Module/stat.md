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

| 功能 | 函数说明 | 备注 |
| :-- | :-- | :-- |
| 事件上报 | ReportEvent | - |
| 事件跟踪 | TrackEventBegin、TrackEventEnd | 两个函数成对出现 |
| 跟踪页面 | TrackPageBegin、TrackPageEnd | 两个函数成对出现 |
| 支付上报 | ReportPurchase | - |
| 网速统计 | SpeedTest | - |
| 开启异常上报 | SetAutoExceptionReport | - |
| 开启崩溃上报 | SetAutoCrashReport | - |







