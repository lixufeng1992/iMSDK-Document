#MTO推送功能说明

##推送支持接口列表

|序号|方法名|方法说明|是否支持| 备注|
|:--|:--|:--|:--|:--|
|1| public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 | √||    
| 2|public bool SetChannel(string channel) | 设置推送渠道，如：XG（信鸽） |√||     
| 3|public string GetChannel() | 获取当前设定渠道 |√||      
| 4|public void Register(string account = "") | 注册 |√||        
| 5|public void SetRegisterCallback(PushCallback callback) | 设定注册回调函数 |√||        
| 6|public void Unregister() | 反注册 | × | |      
| 7|public void SetUnregisterCallback(PushCallback callback) | 反注册回调 | × | |    
| 8|public void SetTag(string tag) | 设定用户标签 | × | |    
| 9|public void SetTag(List< string > tags) | 设定多个用户标签 | × | |     
| 10|public void SetTagCallback(PushCallback callback) | 设定用户标签回调 | × | |   
| 11|public void DelTag(string tag) | 删除标签 | × | |     
| 12|public void DelTag(List< string > tags) | 删除多个标签 | × | |    
| 13|public void SetDelTagCallback(PushCallback callback) | 设定删除标签回调 | × | |   
| 14|public void SetNotifyRecvCallback(PushNotifyCallback callback) | 设定接收推送消息回调 | × | |     
| 15|public void SetNotifyClickCallback(PushNotifyCallback callback) | 设定点击推送消息回调 | × | |    
| 16|public void SetNotifyShowCallback(PushNotifyCallback callback) | 设定推送消息显示回调 | × | |


