## 4.4.13.9 Link功能扩展


### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Link | Link 扩展功能，包括用户社交帐号管理等功能 |

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMLink（GameObject）上，开发者不要主动销毁该对象！</font>


## 模块使用说明

该模块主要用于Link用户管理功能，包括连接社交帐号，获取连接社交帐号状态，恢复社交帐号，删除社交帐号，获取link的AuthToken和设置link的AuthToken等

###调用代码示例
```cs
void OnStart() { 
    IMSDKApi.Link.Initialize ();
}
void OnLink(IMResult result) {
		testInfo = "retcode : " + result.RetCode + "\nmessage : " + result.ErrorMsg;
}
void OnState(IMLinkStateResult result) {
		testInfo = "retcode : " + result.RetCode + "\nmessage : " + result.ErrorMsg + "\nflag : " + result.Result;
}
...

//int itemwidth = Screen.width;
//int itemHeight = Screen.height/20;
if (GUI.Button (new Rect(0,height,itemwidth,itemHeight), "bind sns")) {
    IMSDKApi.Link.Bind(OnLink);
}
		
if (GUI.Button (new Rect(0,height,itemwidth,itemHeight), "delete account")) {
    IMSDKApi.Link.DeleteAccount(OnLink);
}

if (GUI.Button (new Rect(0,height,itemwidth,itemHeight), "restore from sns")) {
    IMSDKApi.Link.RestoreFromSNS(OnState);
}

if (GUI.Button (new Rect(0,height,itemwidth,itemHeight), "get state")) {
    IMSDKApi.Link.QueryConnectState(OnState);
}

if (GUI.Button (new Rect(0,height,itemwidth,itemHeight), "restore from GC")) {
    IMSDKApi.Link.ConnectAndRestoreWithGameCenter(OnState);
}

if (GUI.Button (new Rect (0, height, itemwidth, itemHeight), "getLinkAuthToken")){
    IMSDKApi.Link.GetLinkAuthToken();
}

if (GUI.Button (new Rect (0, height, itemwidth, itemHeight), "setLinkAuthToken")) {
    string linkAuthToken = IMSDKApi.Link.GetLinkAuthToken();
    IMSDKApi.Link.SetLinkAuthToken(linkAuthToken);
}
```

## API参考

| 函数名 | 函数说明 |
| :-- : | :-- : |
| public void Bind(LinkCallback callback = null) | 连接（绑定）社交帐号 <br>  |
| public void DeleteAccount(LinkCallback callback= null) | 删除社交帐号（慎用） |
| public void RestoreFromSNS(LinkStateCallback callback = null) | 从社交平台恢复社交帐号 |
| public void QueryConnectState(LinkStateCallback callback = null) | 查询连接（绑定）状态 |
| public void ConnectAndRestoreWithGameCenter(LinkStateCallback callback = null) |  从GameCenter恢复帐号 | 
| public string GetLinkAuthToken() | 获取用户当前的linkAuthToken |
| public void SetLinkAuthToken(string linkAuthToken) | 设置用户当前的linkAuthToken |


* Link绑定结果结构体 <font color=blue>IMLinkStateResult</font>
> 该结构体继承自IMResult
| 变量 | 说明 |
| :-- | :--: |
| public bool Result | Link绑定状态 |



