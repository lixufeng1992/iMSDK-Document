## 4.4.13.8 Kakao功能扩展

### 基础信息
| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMKakao |iMSDK 的扩展工具|

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMKakao（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门
+ 声明回调函数

```
void OnGetFriend(IMKakaoGetFriendsResult result) {
 IMLog.Log ("get friend callback ...");
 string resultString = result.ToUnityString ();
 IMLog.Log ("result string : " + resultString);
}

void OnResult(IMResult result) {
 IMLog.Log ("operation callback ...");
 string resultString = result.ToUnityString ();
 IMLog.Log ("result string : " + resultString);
}

void OnProfile(IMKakaoUserProfileResult result) {
 IMLog.Log ("profile callback ...");
 string resultString = result.ToUnityString ();
 IMLog.Log ("result string : " + resultString);
}

```

+ 功能调用示例

```
if (GUI.Button (NextRect (), "initailize")) { IMSDKApi.Kakao.Initialize (); }
if (GUI.Button (NextRect (), "get invitable friends")) { IMSDKApi.Kakao.GetInvitableFriends (100, OnGetFriend); }
if (GUI.Button (NextRect (), "get registered friends")) { IMSDKApi.Kakao.GetRegisteredFriends (100, OnGetFriend); }
if (GUI.Button (NextRect (), "is story user")) { IMSDKApi.Kakao.IsStoryUser(OnResult); }
if (GUI.Button (NextRect (), "post story")) { IMSDKApi.Kakao.PostStory("111", "hhhh", OnResult); }
if (GUI.Button (NextRect (), "get talk profile")) { IMSDKApi.Kakao.GetTalkUserProfile (OnProfile); }
if (GUI.Button (NextRect (), "get game profile")) { IMSDKApi.Kakao.GetGameUserProfile (OnProfile); }
if (GUI.Button (NextRect (), "update game profile")) { Dictionary<string, string> properties = new Dictionary<string, string> (); properties.Add ("name", "hahaha"); IMSDKApi.Kakao.UpdateGameUserProfile (properties, OnResult); }
if (GUI.Button (NextRect (), "unlink")) { IMSDKApi.Kakao.Unlink(OnResult); }
```

### 参考

* kakao好友信息结构体 **IMKakaoFriendInfo**
| 变量 | 说明 |
| :-- | :-- |
| public string UserId |  游戏用户ID  |
| public string UuId |  未绑定游戏的用户识别参数  |
| public string ServiceUserId |  kakao会员编号  |
| public string NickName |  kakaotalk昵称  |
| public bool AppRegistered |  好友是否加入游戏  |
| public bool AllowedTalkMessaging |  判断是否允许接收信息  |
| public string ThumbnailURL |  kakaotalk个人信息图片链接，1100px*1100px  |
| public int StoryRelation |  判断是否kakao story关系：0-好友 1-非好友 2-未知  |
| public int TalkOS |  kakaotalk中设备信息：0-未知 1-IOS 2-Androind  |
| public int TalkRelation |  判断是否kakao好友：0-好友 1-非好友 2-未知  |
| public int GroupChatMessageRemainingCount |  今天内可发送聊天室信息的剩余量  |
| public int InviteMessageRemainingCount |  今天可发送邀请信息的剩余量  |

*  kakao个人信息结构体 **IMKakaoUserProfileResult**

| 变量 | 说明 |
| :-- | :-- |
| public string UserId | 游戏用户ID |
| public string UuId | 未绑定游戏的用户识别参数 |
| public string serviceUserId |  kakao会员编号 |
| public string NickName |  kakaotalk昵称 |
| public string ThumbnailImage |  kakaotalk个人信息图片链接，1100px*1100px  |
| public string ProfileImage |  kakaotalk个人信息图片链接，640px*640px  |
| public string CountryISO | kakaotalk国家  |
| public int GroupChatMessageRemainingCount | 今天内可发送聊天室信息的剩余量 |
| public int InviteMessageRemainingCount | 今天可发送邀请信息的剩余量 |

* 接口说明

| 函数名 | 函数说明 |
| :-- | :-- |
| GetInvitableFriends() |  获取kakaotalk好友中未加入游戏的好友列表 |
| GetRegisteredFriends() |  获取kakaotalk好友中加入游戏的好友列表 |
| IsStoryUser() |  查询是否是kakaostory绑定用户  |
| PostStory() |  发送kakao朋友圈 |
| GetTalkUserProfile() |  获取kakaotalk 个人信息(talkProfile) |
| GetGameUserProfile() |  获取个人游戏信息(游戏相关)  |
| UpdateGameUserProfile() |  修改用户字段和用户信息 (key包含有:unique_nickname nickname level exp) |
| unlink() |  kakao用户解绑app  |


###配置说明
#### iOS 配置说明

#### Android 配置说明
