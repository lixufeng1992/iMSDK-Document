## 4.4.9 位置服务(Location)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMLocation |该模块主要用于获取用户的位置信息|

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMLocation（GameObject）上，开发者不要主动销毁该对象！</font>

### 工程配置说明

#### Android工程配置说明

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

#### iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。
    
### 参考

* 位置服务方法类 <font color=blue>IMLocation</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数 |
| public void SetLanguage(int language) | 设定显示语言 |
| public void GetLocation(LocationCallback callback=null, bool realtime = false) | 获取用户地理位置信息 |

### 代码示例

```cs
void Start() {
    IMSDKApi.Location.Initialize ();
}

IMSDKApi.Location.SetLanguage(1);
IMSDKApi.Location.GetLocation();
	
```