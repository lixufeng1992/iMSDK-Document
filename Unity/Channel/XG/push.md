## XG 推送功能说明

### 推送支持接口列表

| 函数名 | 函数说明 | 是否支持 | 备注 |
| -- | -- | -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 | √ | |
| public bool SetChannel(string channel) | 设置推送渠道，如：XG（信鸽） | √ | |
| public string GetChannel() | 获取当前设定渠道 | √ |  |
| public void Register(string account = "") | 注册 | √ | |
| public void SetRegisterCallback(PushCallback callback) | 设定注册回调函数 | √ | |
| public void Unregister() | 反注册 | √ | | 
| public void SetUnregisterCallback(PushCallback callback) | 反注册回调 | √ | |
| public void SetTag(string tag) | 设定用户标签 | √ | |
| public void SetTag(List< string > tags) | 设定多个用户标签 | √ | |
| public void SetTagCallback(PushCallback callback) | 设定用户标签回调 | √ | |
| public void DelTag(string tag) | 删除标签 | √ | |
| public void DelTag(List< string > tags) | 删除多个标签 | √ | |
| public void SetDelTagCallback(PushCallback callback) | 设定删除标签回调 | √ | |
| public void SetNotifyRecvCallback(PushNotifyCallback callback) | 设定接收推送消息回调 | √ | |
| public void SetNotifyClickCallback(PushNotifyCallback callback) | 设定点击推送消息回调 | √ | |
| public void SetNotifyShowCallback(PushNotifyCallback callback) | 设定推送消息显示回调 | √ | |
| public void AddLocalNotification(IMLocalMessage message, Dictionary<string, string> userinfo = null) |本地推送，Android不支持扩展userinfo| × |  |
| public void ClearLocalNotifications() |清空本地通知| × | |
| public void DeleteLocalNotifications(string key) |IOS特有，删除特定的本地通知| × | |


