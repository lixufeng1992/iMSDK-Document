## GDN 功能说明


###1. 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | :--: |:-------: | :-----: | :--: |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | √ | - |
| 3 | public void ReportEvent(string eventName, bool realtime = false) | 事件上报 | x | - |    
|4|public void ReportEvent(string eventName, Dictionary< string, string> paramDict, bool realtime =  false)|上报事件，并设定事件体| √ | |
| 4 | public void ReportPurchase(string purchaseName, string currencyCode, string expense, bool realtime = false) | 购买行为上报 | x | - |
| 5 | public void TrackEventBegin(string eventName, string eventBody) | 事件跟踪开始 | x | - |
| 6 | public void TrackEventEnd(string eventName, string eventBody) | 事件跟踪结束 | x | - |
|8| public void TrackPageBegin(string pageName)|页面跟踪开始|x | - |   
|9|public void TrackPageEnd(string pageName)|页面跟踪结束|x | - |  
||public void SpeedTest(List< string > hostList)|	网络测试| x | - |      
||public void SpeedTest(Dictionary< string, int > hostDict)	|带端口的网络测试|x | - |  
||public void SetAutoExceptionReport(bool enable = false)	|设定异常自动上报开关| x | - | 
||public void SetAutoCrashReport(bool enable = false)|	设定异常退出上报开关| x | - |

###2. 注意      
`ReportEvent(string eventName, Dictionary< string, string> paramDict, bool realtime =  false)`通过eventName来区分转化跟踪与再营销：  

|eventName|功能|    
|:--|:--|
| Conversiontracking|转化跟踪|   
|Remarketing|再营销|    
###3.reportEvent demo:     

```
//转化跟踪 param需要到google adwords官网申请
Dictionary<string, string> param = new Dictionary<string, string>();
param["Label"] = "aaaa";
param["Value"] = "bbbbb";
param["Repeatable"] = "bbbbb";
IMSDKApi.Stat.ReportEvent("Conversiontracking", param,true);
			
//再营销
Dictionary<string, string> param = new Dictionary<string, string>();
param["action_type"]= "page_view";
param["product_category"]="shoes";
param["value"]="15.99";
param["product_id"]="222";
IMSDKApi.Stat.ReportEvent("Remarketing", param,true);
			
```
###4 额外说明
* Android
 游戏需在自己的主Activity中调用下面方法：
 + 1. onCreate中调用 ： ExtendGDNManager.initialize(context);， 如ExtendGDNManager.initialize(getApplicationContext());。
 + 2. onResume()中调用ExtendGDNManager.enableAutomatedUsageReporting();。