## Netmarble 扩展功能说明

### Netmarble Extend 接口列表
|序号|方法名|方法说明|是否支持|备注|
|:--|:--|:--|:--|:--|
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public void ShowTerms(ShowTermsCallback callback = null) | 显示许可协议 | √ | - |
| 4 | public void ConnectChannel(int channelID = 2, ConnectChannelCallback callback = null) | 绑定渠道 | √ | 目前仅支持Kakao（对应channelID = 2） |
| 5 | public void DisconnectFromChannel(int channelID = 2 , NetmarbleCallback callback = null) | 解除绑定渠道 | √ | 目前仅支持Kakao（对应channelID = 2） |
| 6 | public void UnRegisterKakao(NetmarbleCallback callback = null) | 注销Kakao | √ | - |
| 7 | public bool ResetSession() | 重置Session | √ | - |
| 8 | public void RequestKakaoProfile(KakaoProfileCallback callback = null) | 请求用户Kakao信息 | √ | - |
| 9 | public void RequestKakaoFriends(KakaoFriendCallback callback = null) | 请求用户Kakao好友列表 | √ | - |
| 10 | public void ShowMessageBlockDialog (NetmarbleCallback callback) | 显示设置屏蔽消息对话框 | √ | - |
| 11 | public void SetLanguage(string language) | 设置语言 | √ | - |

### Netmarble Extend 接口调用示例
```
void OnShowTerms (int termsState)
{
	testInfo = "授权结果:"
			+ "\n state : " + termsState;
}

void OnConnect (IMNetmarbleConnectResult result)
{
	string playerIDPrompt="";
	if (result.PlayerIDChanged) {
		playerIDPrompt = "playerID Changed";
	} else {
		playerIDPrompt = "playerID not changed";
	}
	testInfo = " OnConnect result:"
		+ "\n " + playerIDPrompt
		+ "\n"  + FormatJson (result.ToUnityString ());
}

void OnDisconnect (IMResult result)
{
	testInfo = " OnDisconnect result:"
	+ "\n"  + FormatJson (result.ToUnityString ());

}

void OnUnRegister(IMResult result)
{
	testInfo = " OnUnRegistor result:"
	+ "\n"  + FormatJson (result.ToUnityString ());
}

void OnRequestKakaoProfile(IMNetmarbleKakaoProfileResult profileResult)
{
	testInfo = " OnRequestKakaoProfile result:"
	+ "\n" + FormatJson (profileResult.ToUnityString ());
}

void OnRequestKakaoFriends(IMNetmarbleKakaoFriendResult friendResult)
{
	testInfo = " OnRequestKakaoFriends result:"
	+ "\n" + FormatJson (friendResult.ToUnityString ());
}

void OnShowMessageBlockDialog(IMResult result) 
{
	testInfo = " OnShowMessageBlockDialog result:"
		+ "\n" + FormatJson (result.ToUnityString ());
}

void Start ()
{
	// 我们建议在游戏开始时就初始化登陆方法
	IMSDKApi.Netmarble.Initialize ()
}

void TestShowTerms(){
	IMSDKApi.Netmarble.ShowTerms (OnShowTerms);
}

void TestConnectChannel(){
	IMSDKApi.Netmarble.ConnectChannel (2,OnConnect);
}

void TestDisconnectFromChannel(){
	IMSDKApi.Netmarble.DisconnectFromChannel (2,OnDisconnect);
}

void TestUnRegisterKakao(){
	IMSDKApi.Netmarble.UnRegisterKakao(OnUnRegister);
}

void TestResetSession(){
	IMSDKApi.Netmarble.ResetSession ();
}

void TestRequestKakaoProfile(){
	IMSDKApi.Netmarble.RequestKakaoProfile (OnRequestKakaoProfile);
}

void TestRequestKakaoFriends(){
	IMSDKApi.Netmarble.RequestKakaoFriends (OnRequestKakaoFriends);
}

void TestShowMessageBlockDialog(){
	IMSDKApi.Netmarble.ShowMessageBlockDialog (OnShowMessageBlockDialog);
}

void TestSetLanguage(){
	IMSDKApi.Netmarble.SetLanguage ("ko-kr");
}

```

### 参考
* ShowTerms返回字段state意义

	| 变量 | 说明 |
	| :-- | :-- |
  | 0 | Opened |
  | 1 | Closed |
  | 2 | Failed |
  | 3 | Rewarded |

* ConnectChannel返回结构体 <font color=blue>IMNetmarbleConnectResult</font>
	
	IMNetmarbleConnectResult 继承自IMResult，添加字段PlayerIDChanged

	| 变量 | 说明 |
	| :-- | :-- |
  | true | connect之后PlayerID变化了 |
  | false | connect之后PlayerID没有变化 |

* RequestKakaoProfile返回结构体<font color = blue>IMNetmarbleKakaoProfileResult</font>
	
	IMNetmarbleKakaoProfileResult继承自IMResult，添加如下字段
	
	| 变量 | 说明 |
	| :-- | :-- |
	| public string PlayerID | Netmarble用户PlayerID |
	| public string KakaoID | Netmarble用户KakaoID |
	| public string KakaoGameID | Netmarble用户KakaoGameID |
	| public string ProfileImageURL | Netmarble用户ProfileImageURL |
	| public string HashedUserKey | Netmarble用户HashedUserKey |
	| public string MessageBlocked | Netmarble用户MessageBlocked（是否屏蔽消息）| 

* RequestKakaoFriends返回结构体<font color = blue> IMNetmarbleKakaoFriendResult</font>

	IMNetmarbleKakaoFriendResult继承自IMResult，添加如下字段
	
	| 变量 | 说明 |
	| :-- | :-- |
	| public List<IMNetmarbleKakaoFriendProfile> InvitableFriendList | Netmarble用户的可邀请好友列表 |
	| public List<IMNetmarbleKakaoFriendProfile> RegisteredFriendList | Netmarble用户的已注册好友列表 |

### 附加说明
* SetLanguage(string language)

	language参数列表
	
	| 参数 | 语言 |
	| :-- | :-- |
	| ko-kr | 韩语 |
	| ja-jp | 日语 |
	| en-us | 英语 | 
	| th-th | 泰语 | 
	| zh-cn | 中文简体 |
	| zh-tw | 中文繁体 | 
	| tr-tr | 土耳其语 |
	| ar-eg | 阿拉伯语 |
	| fr-fr | 法语 |
	| it-it | 意大利语 |
	| de-de | 德语 |
	| es-es | 西班牙语 |
	| pt-pt | 葡萄牙语 |
	| id-id | 印度尼西亚语 |
	| ru-ru | 俄语 |
