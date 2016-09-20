## 4.4.10 帮助反馈(Help)

###1.基础信息

|命名空间	| 调用入口|	使用说明|    
|--:|--:|--:|   
|Tencent.iMSDK|	IMSDKApi.Help|	iMSDK帮助中心|
> 该类自动绑定在Unity的Tencent.iMSDK.IMHelp（GameObject）上，开发者不要主动销毁该对象！    

###2.快速入门        
+ 1.[配置](../Channel/help.md)
+ 2.代码示例
```
   IMSDKApi.Help.Initialize ();
	IMSDKApi.Help.SetChannel("IMSDK");
	IMSDKApi.Help.SetLanguage("en"); // your language， such as en
	IMSDKApi.Help.SetZone("USA"); // your zone, such as USA
	IMSDKApi.Help.SetCharacter("ROLE1");  // your role, such as ROLE1
	IMSDKApi.Help.ShowHelpCenter(OnShowHelpCenter);

	public void OnShowHelpCenter(IMHelpShowResult result){
		
	}
```
###3.参考   
+ 方法      

|方法名|方法说明|   
|:--|:--|   
|public bool Initialize()||   
|	public bool SetChannel(string channel)||   
| public string GetChannel()||  
| public void ShowHelpCenter(IMSDKCallback<IMHelpShowResult> callback = null, string extraJson = "")||  
|public void ShowFAQ(IMSDKCallback<IMHelpShowResult> callback = null, string extraJson = "") || 
|public void ShowCustomerService( IMSDKCallback<IMHelpShowResult> callback = null, string extraJson = "")||
|	public void GetNewMessages(IMSDKCallback<IMHelpGetResult> callback = null, string extraJson = "")||
|public void SetLanguage(string language)||
|public string GetLanguage()|| 
|public void SetZone(string zone)||
|public string GetZone()||
|	public void SetCharacter(string character)|| 
|public string GetCharacter()||
|	public void SetRoleName(string roleName)||
|	public string GetRoleName()||
|public void SetRoleId(string roleId)||
|public string GetRoleId()||
|public void SetServerId(string serverId)||
|	public string GetServerId()||   
|public void SetServerName(string serverName)||   
|public string GetServerName()||    	
|public void SetLevel(string level)||   
|public string GetLevel()||    

+ 结构体 （IMHelpShowResult）  

|属性|说明|   
|:--|:--|   
|state||   
|retCode||
|retMsg||   
|imsdkRetCode||
|imsdkRetMsg||
|thirdRetCode||
|thirdRetMsg||    

+ 结构体（IMHelpGetResult）    

|属性|说明|   
|:--|:--|   
|count||   
|retCode||
|retMsg||   
|imsdkRetCode||
|imsdkRetMsg||
|thirdRetCode||
|thirdRetMsg||   

	
