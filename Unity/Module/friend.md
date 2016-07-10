## 4.4.3 好友模块(Friend)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Friend | 用于获取好友关系，给好友发送邀请、消息等功能 |


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMFriend（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门
1. [完成特定渠道配置](../../Channel/README.md)
2. 代码实例

  ```cs
  // 初始化
  void Start() {
      IMSDKApi.Friend.Initialize ();
      IMSDKApi.Friend.SetChannel("Facebook");
  }

  void TestGetFriendsCallback(IMFriendResult result) {
      if(result.RetCode == 1) {
          Debug.Log("get friend ok");

          foreach(IMFriendInfo item in result.FriendInfoList) {
              Debug.Log("get friend : " + item.OpenId);
          }
      }
      else {
          Debug.Log("get friend error : " + result.ErrorMsg);
      }
  }

  void TestGetFriends() {
      IMSDKApi.Friend.GetFriends(1, 100, TestGetFriendsCallback);
  }

  void TestFriendCallback(IMFriendResult result) {
      if(result.RetCode == 1) {
          Debug.Log("message ok "");
      }
      else {
          Debug.Log("message error : " + result.ErrorMsg);
      }
  }

  void TestInvite() {
      IMFriendContent content = new IMFriendContent();

      content.Type = IMFriendContent.MessageType.LINK_DIALOG;
      content.Title = "this is title";
      content.Content = "this is content";
      content.Link = "http://ieg.qq.com";
      content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
      content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";

      IMSDKApi.Friend.Invite(content, TestFriendCallback);
  }

  void TestSendMessage() {
      IMFriendContent content = new IMFriendContent();

      content.Type = IMFriendContent.MessageType.LINK_DIALOG;
      content.Title = "this is title";
      content.Content = "this is content";
      content.Link = "http://ieg.qq.com";
      content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
      content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";

      IMSDKApi.Friend.SendMessage(content, TestFriendCallback);
  }

  ```

## 参考

* 消息参数类 <font color=blue>IMFriendContent</font>

| 变量 | 说明 |
| -- | -- |
| Type | 分享类型，取值取值可以从 <font color=blue>IMShareContent.MessageType</font> 获取
| Title | 标题（部分分享无效） |
| ~~User~~ | 接收消息用户 |
| Content | 分享内容，为文字 |
| Link | 链接，如： http://www.qq.com |
| ImagePath | 分享图片文件路径，可以是网络上的链接，或者是 Android 或 iOS 可以读取的文件路径 |
| ThumbImage | 缩略图，在WeChat（微信）分享用到 |
| ExtraJson | 附加字段，一般无需赋值，在有特殊说明的功能时填写 |

* 消息类型<font color=blue>IMShareContent.MessageType</font>

| 类型 | 说明 |
| -- | -- |
| ~~ShareType.TEXT~~ | ~~文字，后台无界面~~ |
| ShareType.TEXT_DIALOG | 文本，弹窗 |
| ~~ShareType.LINK~~ | ~~链接，后台无界面~~ |
| ShareType.LINK_DIALOG | 链接，弹窗 |
| ~~ShareType.IMAGE~~ | ~~图片，后台无界面~~ |
| ShareType.IMAGE_DIALOG | 图片，弹窗 |

* 返回结构体 <font color=blue>IMFriendResult</font>

| 类型 | 说明 |
| -- | -- |
| public int RetCode | 返回码，为 1 时表示成功 |
| publit string ErrorMsg | 错误信息 |
| public string OpenId | OpenId，用户游戏账号 | 
| public string Guid | 用户全局ID，用户标识 |
| public string GuidToken | iMSDK 使用的Token |
| public uint GuidTokenExpire | GuidToken 有效时间，从北京时间1970年01月01日08时00分00秒的时间戳 |
| public int ChannelId | iMSDK 渠道 ID |
| public int GameId | iMSDK 游戏 ID |
| public string GuidUserNick | 用户昵称 |
| public string GuidUserBirthday | 用户生日，如：1990-01-01 |
| public int GuidUserSex | 用户性别，0-未知；1-男；2-女 |
| public string GuidUserPortrait | 用户头像地址 |
| public int Count | 好友数量 |
| public List< IMFriendInfo > FriendInfoList | 好友信息列表 |


* 好友信息类 <font color=blue>IMFriendInfo</font>

| 类型 | 说明 |
| -- | -- |
| public string ChannelUserId | 原始渠道用户 ID |
| public string GuidUserName | 好友名 |
| public int GuidUserSex | 好友性别，用户性别，0-未知；1-男；2-女 |
| public String OpenId | 好友 Open ID |
| public String GuidUserPortrait | 好友头像地址 |

* 回调代理函数 <font color=blue>FriendCallback</font>

| 类型 | 说明 |
| -- | -- |
| public delegate void FriendCallback(IMFriendResult result) | 关系链回调函数，返回关系链结果结构体 |

* 关系链方法类 <font color=blue>IMFriend</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 |
| public bool Initialize(string channel) | 初始化，并制定关系链渠道（如Facebook） |
| public bool SetChannel(string channel) | 设置关系链渠道 |
| public string GetChannel() | 获取当前设定渠道 |
| public void GetFriends(<br> &emsp;&emsp;int page, int count,<br> &emsp;&emsp;FriendCallback callback<br>&emsp;&emsp;) | 获取好友列表<br> page 为起始页数，从 1 开始<br> count 为每页好友数<br> callback 为关系链回调函数 |
| public void Invite(<br> &emsp;&emsp;IMFriendContent content, <br> &emsp;&emsp;FriendCallback callback=null<br>&emsp;&emsp;) | 邀请好友<br> content 为消息参数，具体参见 IMFriendContent 说明<br> callback 为发送消息回调 |
| public void SendMessage(<br> &emsp;&emsp;IMFriendContent content, <br> &emsp;&emsp;FriendCallback callback=null<br>&emsp;&emsp;) | 给好友发消息 <br> content 为消息参数，具体参见 IMFriendContent 说明<br> callback 为发送消息回调 |