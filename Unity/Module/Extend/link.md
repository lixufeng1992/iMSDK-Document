## 4.4.13.9 Link功能扩展


### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Kakao | Kakao 扩展功能，包括用户用户信息、资料管理等 |

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMKakao（GameObject）上，开发者不要主动销毁该对象！</font>


## 模块使用说明

该模块主要用于获取 Kakao 好友列表，发送 Kakao Story，管理用户资料这几部分功能

### 获取可以邀请好友说明

安装 Kakao 的邀请逻辑，在邀请之前，需要先获取可邀请好友，只能向可邀请好友发送消息，所以在调用 Kakao 好友之前调用获取可邀请好友，这样才能保证能够正常发送邀请：

```cs
protected bool loadKakaoFriend = false;

void OnStart() { 
    IMSDKApi.Friend.Initialize(); 
    IMSDKApi.SetChannel("Kakao"); IMSDKApi.Kakao.Initialize();
}

void OnGetFriend(IMKakaoGetFriendsResult result) { 
    if(result.RetCode == 1) { 
        loadKakaoFriend = true; 
    }
}
...

if(loadKakaoFriend) { 
    IMSDKApi.Friend.Invite(content, callback);
}
```
如果没有获取可邀请好友，直接发送邀请，会返回参数错误

## 参考

* Kakao好友信息结构体 <font color=blue>IMKakaoFriendInfo</font>

| 变量 | 说明 |
| :-- | :-- |
| public string UserId | Kakao 用户 ID |
| public string UuId | Kakao 用户 UUID |
| public string ServiceUserId | Kakao 好友用户ID，只针对特定的App有效<br>(친구의 카카오 회원번호. 앱의 특정 카테고리나 특정 권한에 한해 내려줌) |
| public string NickName | 好友昵称 |
| public bool AppRegistered | 是否注册App |
| public bool AllowedTalkMessaging | 是否接收 Talk 消息通知 |
| public string ThumbnailURL | KakaoTalk头像地址，110px x 110px |
| public int StoryRelation | Story 好友关系：0-好友，1-非好友，2-未知 |
| public int TalkOS | Talk 操作系统：1-iOS，2-Android，3-其他 |
| public int TalkRelation | Talk 好友关系：0-好友，1-非好友，2-未知 |
| public int GroupChatMessageRemainingCount | 【iOS】剩余群发消息数量<br>(남은 일별 그룹 메시지 전송 횟수,TALK_MESSAGE_SEND permission이 있는 경우에만 내려 줌.) |
| public int InviteMessageRemainingCount | 【iOS】剩余邀请消息数量<br>(남은 일별 초대 메시지 전송 횟수,TALK_MESSAGE_SEND permission이 있는 경우에만 내려 줌.) | 

* Kakao 好友信息返回结果 <font color=blue>IMKakaoGetFriendsResult</font>

| 变量 | 说明 |
| :-- | :-- |
| public int RetCode | 返回码 |
| public string ErrorMsg | 错误信息 |
| public List< IMKakaoFriendInfo > Friendlist| Kakao 好友信息列表|

* Kakao 用户资料返回结果 <font color=blue>IMKakaoUserProfileResult</font>

| 变量 | 说明 |
| -- | -- |
| public string UserId | Kakao 用户 ID |
| public string UuId | Kakao 用户 UUID |
| public string ServiceUserId | Kakao 好友用户ID，只针对特定的App有效<br>(친구의 카카오 회원번호. 앱의 특정 카테고리나 특정 권한에 한해 내려줌) |
| public string NickName | 好友昵称 |
| public string ProfileImage | 用户头像 |
| public string ThumbnailURL | KakaoTalk头像地址，110px x 110px |
| public string CountryISO | 国家代码 |
| public int GroupChatMessageRemainingCount | 【iOS】剩余群发消息数量<br>(남은 일별 그룹 메시지 전송 횟수,TALK_MESSAGE_SEND permission이 있는 경우에만 내려 줌.) |
| public int InviteMessageRemainingCount | 【iOS】剩余邀请消息数量<br>(남은 일별 초대 메시지 전송 횟수,TALK_MESSAGE_SEND permission이 있는 경우에만 내려 줌.) |

* Kakao 扩展方法类 <font color=blue>IMKakao</font>

| 函数名 | 函数说明 |
| :-- | :-- |
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数 |
| public void GetInvitableFriends(int count, KakaoGetFriendsCallbck callback) | 获取可邀请好友列表 |
| public void GetRegisteredFriends(int count, KakaoGetFriendsCallbck callback) | 获取已注册好友列表 |
| public void IsStoryUser(KakaoCallback callback) | 是否为Story用户 |
| public void PostStory(string templateId, string content, KakaoCallback callback) | 发送 Kakao Story |
| public void GetTalkUserProfile(KakaoUserProfileCallback callback) | 获取用户Talk资料 |
| public void GetGameUserProfile(KakaoUserProfileCallback callback) | 获取用户游戏资料 |
| public void UpdateGameUserProfile(Dictionary< string, string > properties, KakaoCallback callback) | 更新用户游戏资料 |
| public void Unlink(KakaoCallback callback) | 解绑（注销）Kakao |