# Stove登录模块

## 支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :-- | :-- | :-- | :-- | :-- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(string channel) | 初始化，并制定登录渠道 |√ | |
| 3 | public bool SetChannel(string channel) | 设置登录渠道| √ | |
| 4 | public string GetChannel() | 获取当前设定渠道 | √ | |
| 5 | public void SetType(string type) | 复杂渠道设置登录类型 | √ | |
| 6 | public void Login( <br>&emsp;&emsp;LoginCallback callback = null,<br> &emsp;&emsp;List< string > permissionList = null,<br>&emsp;&emsp;bool needGuid = true) | 一般登录 | √ | |
| 7 | public void StrictLogin( <br>&emsp;&emsp;LoginCallback callback = null,<br> &emsp;&emsp;List< string > permissionList = null,<br>&emsp;&emsp;bool needGuid = true) | 严格登录 | √ | |
| 8 | public void QuickLogin(LoginCallback callback = null) | 快速登录 | √ | |
| 9 | public bool IsLogin() | 判断用户是否已经登录 | √ | |
| 10 | public void AutoLogin(LoginCallback callback = null) | 自动登录 | √ | |
| 11 | public IMLoginResult GetLoginResult() | 获取当前登录返回数据 | √ | |
| 12 | public void Logout() | 登出当前渠道 | √ | |
| 13 | public void Bind(string channel, LoginCallback callback = null) | 绑定到其他渠道账号 | √ | |
| 14 | public void GetBindInfo(BindInfoCallback callback=null) | 获取用户绑定渠道资料 | √ | |
| 15 | public void SetPlayingReportChannel(string channel) | 设定状态上报渠道 | × | |
| 16 | public void ActivatePlayingReport(string extraJson="") | 上报状态 | × | |
| 17 | public void DeactivatePlayingReport() | 关闭状态上报 | × | |
| 18 | public bool IsChannelAppInstalled() | 是否安装渠道应用 | × | |
| 19 | public bool IsChannelSupportApi() | 应用API版本是否可用 | × | - |
| 20 | <font color=red>public void Bind(string channel, LoginCallback callback = null,string subChannel = "",string extrasJsonString = "") </font>| 绑定到第三方子渠道 | √ | |

## 工程配置

 [Stove Android工程配置](../Channel/Stove/android.md)

## 代码示例
```cs
/*
*Stove返回4种登录渠道
* STV_GU ： Stove游客
* STV : Stove
* STV_FB ：Stove Facebook
* STV_GP : Stove Google+
*/
void Start() {
     IMSDKApi.Login.Initialize ();
     IMSDKApi.Login.SetChannel("Stove");
}

 void TestLoginCallback(IMLoginResult result) {
     if(result.RetCode == 1) {
         Debug.Log("login ok, user open id is " + result.OpenId);
         } else {
         Debug.Log("login error : " + result.ErrorMsg);
         }
 }

 void TestLogin() {
     List<string> permissionList = new List<string>();
     permissionList.Add("email");

     IMSDKApi.Login.Login(TestLoginCallback, permissionList, true);
 }
 ```

 以下为Android代码，非Unity代码，Android侧特别注意：由于Garena需要调用生命周期，所以提供下面方法
 - 方法1：
 游戏继承iMSDK提供的Activity:com.tencent.imsdk.unity.garena.UnityPlayerNativeActivity
 - 方法2：
 业务在自己的主Activity中调用


 ```java
 public class YourMainActivity extends Activity{

 @Override
 protected void onCreate(Bundle savedInstanceState) {
 ...
     IMSDKExtendGarena.initialize(this);
 ...
 }

 @Override
 protected void onDestroy() {
     IMSDKExtendGarena.onDestroy();
     super.onDestroy();
 }

 @Override
 protected void onPause() {
     super.onPause();
     IMSDKExtendGarena.onPause();
 }

 @Override
 protected void onResume() {
     super.onResume();
     IMSDKExtendGarena.onResume();
 }

 @Override
 protected void onActivityResult(int requestCode, int resultCode, Intent data) {
 IMSDKExtendGarena.onActivityResult(requestCode, resultCode, data);
 }
```

