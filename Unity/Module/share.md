## 4.4.2 分享模块(Share)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Share |用于用户分享、邀请好友、给好友发消息等社交功能|
    


#### 分享类型说明

分享一般分为两类：

* 后台分享，调用Api后直接分享，在应用后台执行并无弹窗
* 弹窗分享，调用Api后弹出分享框，用户需要进一步操作才能分享

在<font color=blue>IMShareContent.ShareType</font>中定义了iMSDK支持的分享类

### 工程配置说明

#### Android工程配置说明

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

#### iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。

### 参考

* 分享参数类 <font color=blue>IMShareContent</font>

| 变量 | 说明 |
| -- | -- |
| Type | 分享类型，取值取值可以从 <font color=blue>IMShareContent.ShareType</font> 获取 |
| Title | 标题（部分分享无效） |
| Content | 分享内容，为文字 |
| Link | 链接，如： http://www.qq.com |
| ImagePath | 分享图片文件路径，可以是网络上的链接，或者是 Android 或 iOS 可以读取的文件路径 |
| ThumbImage | 缩略图，在WeChat（微信）分享用到 |
| ExtraJson | 附加字段，一般无需赋值，在有特殊说明的功能时填写 |

* 分享类型 <font color=blue>IMShareContent.ShareType</font>

| 类型 | 说明 |
| -- | -- |
| ShareType.TEXT | 文字，后台分享无界面 |
| ShareType.TEXT_DIALOG | 文本，弹窗分享 |
| ShareType.LINK | 链接，后台无界面 |
| ShareType.LINK_DIALOG | 链接，弹窗分享 |
| ShareType.IMAGE | 图片，后台无界面 |
| ShareType.IMAGE_DIALOG | 图片，弹窗分享 |

* 返回结构体 <font color=blue>IMResult</font>

| 变量 | 说明 |
| -- | -- |
| public int RetCode | 分享状态码，1为成功分享，其他为失败 |
| public string ErrorMsg | 错误信息 |

* 回调代理函数 <font color=blue>ShareCallback</font>

| 类型 | 说明 |
| -- | -- |
| public delegate void ShareCallback(IMResult result) | 分享回调函数，返回分享结果结构体 |

* 分享方法类 <font color=blue>IMShare</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前需要调用该函数 |
| public bool Initialize(string channel) | 初始化，并制定分享渠道（如Facebook） |
| public bool SetChannel(string channel) | 设置分享渠道 |
| public string GetChannel() | 获取当前设定渠道 |
| public void Share(<br> &emsp;&emsp;IMShareContent content, <br> &emsp;&emsp;ShareCallback callback = null) | 分享函数<br> content 为分享参数，具体参见 IMShareContent 说明<br> callback 为分享回调 |



### 代码示例

	
```cs
void Start() {
    IMSDKApi.Share.Initialize ();
    IMSDKApi.Share.SetChannel("Facebook");
}

void TestShareCallback(IMResult result) {
    if(result.RetCode == 1) {
        Debug.Log("share ok");
    }
    else {
        Debug.Log("share error : " + result.ErrorMsg);
    }
}

void TestShare() {

    content.Type = IMShareContent.ShareType.LINK_DIALOG;
    content.Title = "this is title";
    content.Content = "this is content";
    content.Link = "http://ieg.qq.com";
    
    /*
    *iMSDK支持3种地址：
    *1.网络地址：以http打头
    *2.本地媒体，如手机相册:以content打头
    *3.本地决对路径：以file打头
    */
    content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
    content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";
    //content.ThumbImage = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg;

    IMSDKApi.Share.Share(content, TestShareCallback);
}

```
