## 4.4.5 推送模块(Push)

### 基础信息

|命名空间|调用用入口|模块说明|
|:--|:--|:--|
|Tencent.iMSDK|IMSDKApi.Push|该类自动绑定在Unity的Tencent.iMSDK.IMPush（GameObject）上<br> 开发者不要主动销毁该对象|

### 快速入门

1. #### [选择渠道，完成配置](../../Channel/README.md)
2. #### 代码实例，如下代码块实现到Google Play进行[OBB](https://developer.android.com/google/play/expansion-files.html)的下载

```
   
//当前下载状态回调
bool OnDownloadStateChanged(IMDownloadState state){
	return false;
}
	
//当前文件的下载进度以及当前下载文件的总大小
void OnDownloadProgress(int curProgress, int total){
}

//在下载前提示用户，即将要下载文件的大小
//<code> true </code> 接受大小继续下载
//<code> false </code> 暂停下载
bool IsAcceptedOBB(string length){
    return false;
}

void OnStart(){

    //设置下载前回调，通知用户即将下载的OBB包大小（可选）
    IMSDKApi.ExpansionFilesDownload.preSetUserConfirmListener (IsAcceptedOBB);

    // publickey 在注册Google Play Console的时候，由Google提供 
    string publickey = {Your Public Key};

    // 盐值就是一些随机数，最好是每次都随机生成
    //Note : byte in C# is Unsigned 8-bit integer, so its range is  0 ~ 255
    byte[] SALT = new byte[] { 1, 42, 12, 1, 54, 98,
			100, 12, 43, 2, 8, 4, 9, 5, 106, 107, 33, 45, 1, 84
    };

    IMSDKApi.ExpansionFilesDownload.onPreExcuteGoogleDownloader (publickey, SALT);

    // “GSDKTester” : OBB 下载完成后需要跳转到的场景
    // "Google" : 表明从Google Play下载OBB包
    IMSDKApi.ExpansionFilesDownload.Initialize ("GSDKTester", OnDownloadStateChanged, OnDownloadProgress, "Google");
}

```

### 参考

* IMExpansionFilesDownload

|函数名|函数说明|
|:--|:--|
|public void PreSetUserConfirmListener(AcceptedOBBDelegate acceptedOBB)|获取OBB包大小之后，并且在OBB包进行下载前的确认回调|
|public void OnPreExcuteGoogleDownloader(string publickey, byte[] salt)|到Google Play上进行OBB下载的特有方法|
|public void Initialize(string nextScene, <br>DownloadStateChangeDelegate stateChangedCallback = null, <br>DownloadProgressDelegate progressCallback = null, <br>string tag = "IMSDK")|初始化<br> 1. nextScene : OBB包下载完成后需要调整的场景 <br> 2. tag : 表明需要从哪里进行OBB包下载，目前只有两个值 “IMSDK” 跟“Google” |
|public bool IsUnityApkUseObb()|判断当前的APK是否使用分包功能|
|public void RequestPauseDownload()|暂停当前的下载|
|public void RequestContinueDownload()|继续当前下载|
|public void RequestAbortDownload()|放弃当前的下载，无法再继续，需要从新开始下载|

* IMDownloadState 下载状态码

|状态码|状态码对应值|
|:--|:--:|
|UNKNOWN_STATE|-1|
|SERVICE_CONNECTED|10000|
|IDLE | 1|
|FETCHING_URL | 2|
|CONNECTING | 3|
|DOWNLOADING | 4|
|COMPLETED | 5|
|PAUSED_NETWORK_UNAVAILABLE | 6|
|PAUSED_BY_REQUEST | 7|
|PAUSED_WIFI_DISABLED_NEED_CELLULAR_PERMISSION | 8|
|PAUSED_NEED_CELLULAR_PERMISSION | 9|
|PAUSED_WIFI_DISABLED | 10|
|PAUSED_NEED_WIFI | 11|
|PAUSED_ROAMING | 12|
|PAUSED_NETWORK_SETUP_FAILURE | 13|
|PAUSED_SDCARD_UNAVAILABLE | 14|
|FAILED_UNLICENSED | 15|
|FAILED_FETCHING_URL | 16|
|FAILED_SDCARD_FULL | 17|
|FAILED_CANCELED | 18|
|FAILED | 19|

### 代码示例

* 到Google Play进行下载

```
   
//当前下载状态回调
bool OnDownloadStateChanged(IMDownloadState state){
	return false;
}
	
//当前文件的下载进度以及当前下载文件的总大小
void OnDownloadProgress(int curProgress, int total){
}

//在下载前提示用户，即将要下载文件的大小
//<code> true </code> 接受大小继续下载
//<code> false </code> 暂停下载
bool IsAcceptedOBB(string length){
    return false;
}

void OnStart(){

    //设置下载前回调，通知用户即将下载的OBB包大小（可选）
    IMSDKApi.ExpansionFilesDownload.preSetUserConfirmListener (IsAcceptedOBB);

    // publickey 在注册Google Play Console的时候，由Google提供 
    string publickey = {Your Public Key};

    // 盐值就是一些随机数，最好是每次都随机生成
    //Note : byte in C# is Unsigned 8-bit integer, so its range is  0 ~ 255
    byte[] SALT = new byte[] { 1, 42, 12, 1, 54, 98,
			100, 12, 43, 2, 8, 4, 9, 5, 106, 107, 33, 45, 1, 84
    };

    IMSDKApi.ExpansionFilesDownload.onPreExcuteGoogleDownloader (publickey, SALT);

    // “GSDKTester” : OBB 下载完成后需要跳转到的场景
    // "Google" : 表明从Google Play下载下载OBB包
    IMSDKApi.ExpansionFilesDownload.Initialize ("GSDKTester", OnDownloadStateChanged, OnDownloadProgress, "Google");
}

```

* 到IMSDK 后台进行下载

```
   
//当前下载状态回调
bool OnDownloadStateChanged(IMDownloadState state){
	return false;
}
	
//当前文件的下载进度以及当前下载文件的总大小
void OnDownloadProgress(int curProgress, int total){
}

//在下载前提示用户，即将要下载文件的大小
//<code> true </code> 接受大小继续下载
//<code> false </code> 暂停下载
bool IsAcceptedOBB(string length){
    return false;
}

void OnStart(){

    //设置下载前回调，通知用户即将下载的OBB包大小（可选）
    IMSDKApi.ExpansionFilesDownload.preSetUserConfirmListener (IsAcceptedOBB);

    // 设置后台服务器地址，OBB包最终需要放在这里
    IMSDKApi.ExpansionFilesDownload.setCustomFetchURL ("http://www.aeonme.com/speed/");
    
    // “GSDKTester” : OBB 下载完成后需要跳转到的场景
    // "IMSDK" : 表明从IMDSK 的服务器下载OBB包
    IMSDKApi.ExpansionFilesDownload.Initialize ("GSDKTester", OnDownloadStateChanged, OnDownloadProgress, "IMSDK");
}

```