##Netmarble 好友说明

###Friend接口支持情况

|序号|方法名|方法说明|是否支持|备注|
|:--|:--|:--|:--|:--|
| 1|public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 |√ | - |
| 2|public bool Initialize(string channel) | 初始化，并制定关系链渠道（如Facebook） |√ | - |
| 3|public bool SetChannel(string channel) | 设置关系链渠道 |√ | - |
| 4|public string GetChannel() | 获取当前设定渠道 |√ | - |
| 5|public void GetFriends(<br> &emsp;&emsp;int page, int count,<br> &emsp;&emsp;FriendCallback callback<br>&emsp;&emsp;) | 获取好友列表<br> page 为起始页数，从 1 开始<br> count 为每页好友数<br> callback 为关系链回调函数 |x | - |
| 6|public void Invite(<br> &emsp;&emsp;IMFriendContent content, <br> &emsp;&emsp;FriendCallback callback=null<br>&emsp;&emsp;) | 邀请好友<br> content 为消息参数，具体参见 IMFriendContent 说明<br> callback 为发送消息回调 |√ | - |
| 7|public void SendMessage(<br> &emsp;&emsp;IMFriendContent content, <br> &emsp;&emsp;FriendCallback callback=null<br>&emsp;&emsp;) | 给好友发消息 <br> content 为消息参数，具体参见 IMFriendContent 说明<br> callback 为发送消息回调 |√ | - |

其中7 发送消息接口 支持情况如下

| 序号 | 功能 | 是否支持 | 备注 |
| :-- | :-- | :-- | :-- |
| 1 | 发送文本-后台 | √ | - |
| 2 | 发送文本-对话框 | √ | 可以调用，但是表现形式还是静默发送 |
| 3 | 发送链接-后台 | x | - |
| 4 | 发送链接-对话框 | x | - |
| 5 | 发送图片-后台 | √ | - |
| 6 | 发送图片-对话框 | √ | 可以调用，但是表现形式还是静默发送 |

发送消息接口字段填写规则

| 消息类型 | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson） |
| :--: | :--: | :--: | :--: | :--: | :--: | -- |
| 邀请 | - | - | - | √（可选）| - | √ |
| 文本（后台） | - | √ | - | - | - | - |
| 文本（对话框） | x | x | x | x | x | - |
| 链接（后台） | √ | √ | √ | √（网络链接） | - | 接收消息好友列表 |
| 链接（对话框） | √ | √ | √ | √（网络链接） | - | 接收消息好友列表 |
| 图片（后台） | - | - | - | √（本地路径）| - | 接收消息好友列表 |
| 图片（对话框） | - | - | - | √（本地路径）| - | 接收消息好友列表 |

### ExtraJson格式
```
{
    "templateID":"123",
    "templateContent":
    {
        "key1":"value1",
        "key2":"value2"
    }
}
```
