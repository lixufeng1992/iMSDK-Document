##MTO 好友说明
###Friend接口支持情况
| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1|public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 |
| 2|public bool Initialize(string channel) | 初始化，并制定关系链渠道（如Facebook） |
| 3|public bool SetChannel(string channel) | 设置关系链渠道 |
| 4|public string GetChannel() | 获取当前设定渠道 |
| 5|public void GetFriends(<br> &emsp;&emsp;int page, int count,<br> &emsp;&emsp;FriendCallback callback<br>&emsp;&emsp;) | 获取好友列表<br> page 为起始页数，从 1 开始<br> count 为每页好友数<br> callback 为关系链回调函数 |
| 6|public void Invite(<br> &emsp;&emsp;IMFriendContent content, <br> &emsp;&emsp;FriendCallback callback=null<br>&emsp;&emsp;) | 邀请好友<br> content 为消息参数，具体参见 IMFriendContent 说明<br> callback 为发送消息回调 |
| 7|public void SendMessage(<br> &emsp;&emsp;IMFriendContent content, <br> &emsp;&emsp;FriendCallback callback=null<br>&emsp;&emsp;) | 给好友发消息 <br> content 为消息参数，具体参见 IMFriendContent 说明<br> callback 为发送消息回调 |