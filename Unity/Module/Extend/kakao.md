## 4.4.13.8 Kakao功能扩展

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