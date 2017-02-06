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



###关于MTO ShowHelpCenter参数具体说明

* extrajson格式：



 ```json

 {

 guild : xxxx

 content : xxxx

 }

 ```



###SET接口说明

如果拉出帮助中心，需要传入roleName， level， serverId等值，需要在调showHelpCenter接口前，调用对应的set接口。

```

SetLevel(string level);

SetRoleName(string roleName);

SetServerId(string serverId);

```






