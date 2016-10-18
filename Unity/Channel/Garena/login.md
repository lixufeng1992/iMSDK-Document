# Garena登录模块

## 支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
|  :--  |  :--  | :--  |  :--  |  :--  |
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

```cs
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
 package="com.tencent.imsdk.your.packagename"
 android:versionCode="1"
 android:versionName="1.0" >

 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="com.android.vending.BILLING" />
 <uses-permission android:name="android.permission.READ_LOGS" />
 <uses-permission android:name="android.permission.WAKE_LOCK" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />

 <application
 android:allowBackup="false"
 android:icon="@drawable/ic_launcher"
 android:label="@string/app_name" >

 <meta-data
 android:name="com.tencent.imsdk.garena.Environment"
 android:value="test" /><!-- production -->
 <meta-data
 android:name="com.tencent.imsdk.garena.APP_SDK_KEY"
 android:value="{your_garena_app_sdk_key}" />
 <meta-data
 android:name="com.garena.sdk.applicationId"
 android:value="{your_garena_sdk_applicationId}" />
 <meta-data
 android:name="com.garena.sdk.ApplicationSourceId"
 android:value="2" />
 <!-- application id must be filled to use garena service. many APIs depend on this id, please contact garena mobile game team to get this id -->
 <meta-data
 android:name="com.garena.sdk.applicationId"
 android:value="{your_garena_sdk_applicationId}" />
 <!-- same as application id. need to specify for push notification service to work -->
 <meta-data
 android:name="com.garena.sdk.push.applicationId"
 android:value="{your_garena_sdk_applicationId}" />
 <meta-data
 android:name="com.beetalklib.ganalytics.report_url"
 android:value="http://122.11.128.69:2205" />

 <!-- Common login entry activity, the orientation must be specified as portrait or landscape, it can't be specified as sensorLanscape -->
 <activity
 android:name="com.beetalk.sdk.BTLoginActivity"
 android:screenOrientation="portrait"
 android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />

 <!-- BeeTalk Login start -->
 <!-- If enable BeeTalk Login, please register this activity -->
 <activity
 android:name="com.beetalk.sdk.BTBeeTalkAuthActivity"
 android:screenOrientation="portrait" />
 <!-- Facebook App ID unique for each game. Please apply a facebook id on facebook website
 -->
 <meta-data
 android:name="com.facebook.sdk.ApplicationId"
 android:value="@string/facebook_app_id" />

 <activity
 android:name="com.facebook.FacebookActivity"
 android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
 android:label="@string/app_name"
 android:theme="@android:style/Theme.Translucent.NoTitleBar" />

 <provider
 android:name="com.facebook.FacebookContentProvider"
 android:authorities="com.facebook.app.FacebookContentProvider{your_facebook_id}"
 android:exported="true" />
 <!-- Facebook Login end -->


 <!-- Garena Login start -->
 <activity
 android:name="com.beetalk.sdk.GarenaAuthActivity"
 android:screenOrientation="portrait" />
 <!-- Garena Login end -->

 <activity
 android:name="com.beetalk.sdk.plugin.GGPluginActivity"
 android:configChanges="orientation|screenSize"
 android:screenOrientation="portrait"
 android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />

 <!-- Garena Payment Start -->
 <activity
 android:name="com.garena.pay.android.GGPayActivity"
 android:configChanges="orientation"
 android:exported="true"
 android:launchMode="singleTop"
 android:screenOrientation="portrait"
 android:theme="@style/Theme.Transparent" />
 <!-- Garena Payment End -->

 <receiver
 android:name="com.garena.android.gpns.logic.AlarmReceiver"
 android:process="com.garena.msdk.pushservice2" >
 <intent-filter>
 <action android:name="com.garena.android.gpns.ALARM_ACTION100050" />
 </intent-filter>
 </receiver>

 <service
 android:name="com.garena.android.gpns.GNotificationService"
 android:enabled="true"
 android:exported="true"
 android:process="com.garena.msdk.pushservice2" >
 <intent-filter>
 <action android:name="com.garena.android.gpush.GNotificationService" />
 </intent-filter>
 </service>

 <receiver
 android:name="com.garena.android.DefaultNotificationReceiver"
 android:enabled="true"
 android:exported="true" >
 <intent-filter>
 <action android:name="com.garena.android.gpns.NOTIFICATION_RECEIVE" />

 <category android:name="com.garena.garena_msdk_sample.app" />
 </intent-filter>
 </receiver>

 <service
 android:name="com.garena.android.gpns.strategy.ServiceLoaderIntentService"
 android:exported="false" />

 <receiver
 android:name="com.garena.android.gpns.logic.UninstallReceiver"
 android:enabled="true"
 android:exported="true" >
 <intent-filter>
 <category android:name="android.intent.category.DEFAULT" />

 <action android:name="android.intent.action.PACKAGE_REMOVED" />

 <data android:scheme="package" />
 </intent-filter>
 </receiver>
 <receiver android:name="com.garena.android.gpns.logic.RebootReceiver">
 <intent-filter>
 <action android:name="android.intent.action.BOOT_COMPLETED"/>
 </intent-filter>
 <intent-filter>
 <action android:name="android.intent.action.EXTERNAL_APPLICATIONS_AVAILABLE"/>
 </intent-filter>
 </receiver>

 <receiver
 android:name="com.garena.android.gpns.strategy.RemoteQueryReceiver"
 android:process="com.garena.msdk.pushservice3">
 <intent-filter>
 <action android:name="com.garena.android.gpns.enquiry"/>
 </intent-filter>
 </receiver>
 </application>

</manifest>
```

## 代码示例


```cs
void Start() {
    IMSDKApi.Login.Initialize ();
    IMSDKApi.Login.SetChannel("Garena");

    /*
     *Garena有4子渠道，
     *GRN_BT:Garena-Beetalk渠道
     *GRN_GU:Garena-Guest渠道
     *GRN_FB:Garena-Facebook渠道
     *GRN_Gas:Garena-本身渠道
     */
    IMSDKApi.Login.SetType("GRN_BT");
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

