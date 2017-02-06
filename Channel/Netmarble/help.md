## Netmarble 帮助系统说明

### 登录支持接口列表
|序号|方法名|方法说明|是否支持|备注|
|:--|:--|:--|:--|:--|
| 1 | public bool Initialize() | 初始化方法 | √ | - |
|2|public void Send(string content)|发关反馈|×|-|
|3|public void GetNewMessageCount(FeedbackCallback callback)|获取最新反馈|×| - |
|4|public void SetLanguage(string language)|设置语言|×|-|
|5|public void ShowHelpCenter(string channel = "IMSDK")|显示帮助中心|×|-|
|6|public void SetChannel(string channel = "IMSDK")|设置渠道|√| 设置为'Netmarble'|
|7|public string GetLanguage()|获取语言|×|-|
|8| public void SetZone(string zone)|设置大区|×|-|
|9|public string GetZone()|获取大区|×|-|
|10|public void SetRoleName(string roleName)|设置角色名|x|-|
|11|public string GetRoleName()|获取角色名|×|-|
|12|public void SetRoleId(string roleId)|设置角色ID|×|-|
|13| public string GetRoleId()|获取角色ID|x|-|
|14|public void SetServerId(string serverId)|设置服务器ID|x|-|
|15|public string GetServerId()|获取服务器ID|x|-|
|16| public void SetServerName(string serverName)|设置服务器名|x|-|
|17|public string GetServerName()|获取服务器名|x|-|
|18| public void SetLevel(string level)|设置级别|x|-|
|19| public string GetLevel()|获取级别|x|-|
|20|public void ShowHelpCenter(string extraJson,string channel,HelpCallback callback = null)|显示帮助中心|√|-|
|21|public void ShowFAQ(string extraJson = "",HelpCallback callback = null)|显示FAQ|x|-|
|22|public void ShowCustomerService(string extraJson = "",HelpCallback callback = null)|显示用户中心|x|-|

### ShowHelpCenter接口extrajson格式：
```json
{    
"location":12001
}
```

location 参数意义如下

* 12001 --- CustomerSupport.HOME: 客服中心主页

* 12002 --- CustomerSupport.FAQ: 经常提问内容

* 12003 --- CustomerSupport.INQUIRY: 我的询问记录

* 12004 --- CustomerSupport.GUIDE: 指南

* 12005 --- CustomerSupport.INQUIRY_HISTOR: 我的询问记录






