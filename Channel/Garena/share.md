# Garena分享模块

## 分享功能支持列表

| 序号 | 功能 | 是否支持 | 备注 |
| --- | --- | --- | --- |
| 1 | 分享文本-后台 | x | 需要publish\_actions权限 |
| 2 | 分享文本-对话框 | √ | - |
| 3 | 分享链接-后台 | x | 需要publish\_actions权限 |
| 4 | 分享链接-对话框 | √ | - |
| 5 | 分享图片-后台 | x | 需要publish\_actions权限 |
| 6 | 分享图片-对话框 | √ | - |

## 字段填写规则

| 分享类型 | 标题（Title） | 内容（Content） | 链接（Link） | 图片（ImagePath） | 缩略图（ThumbPath） | 扩展字段（ExtraJson） |
| --- | --- | --- | --- | --- | --- | --- |
| 文本（后台） | - | √ | - | - | - | - |
| 文本（对话框） | x | x | x | x | x | - |
| 链接（后台） | √ | √ | √ | √（网络链接） | - | 接收消息好友列表 |
| 链接（对话框） | √ | √ | √ | √（网络链接） | - | 接收消息好友列表 |
| 图片（后台） | - | - | - | √（本地路径） | - | 接收消息好友列表 |
| 图片（对话框） | - | - | - | √（本地路径） | - | 接收消息好友列表 |

扩展字段使用说明：

* 接收消息好友列表

  以JSON格式字符串传值，如：

  ```json
  {"friends":["123","234"]}
  ```


## 工程配置

### Android工程配置

```xml
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
 android:value="{your_garena_sdk_applicationId} />
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

### iOS工程配置

按Garena工程通用配置进行配置即可

## 代码示例

```cs
 void Start() {
 IMSDKApi.Share.Initialize ();
 IMSDKApi.Share.SetChannel("Garena");
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
 testGarenaShareTextDialog();//分享TextDialog
 testGarenaShareLinkDialog();//分享LinkDialog
 testGarenaShareImageDialog();//分享ImageDialog
}

 private IMShareContent createDemoShareContent(){
 IMShareContent content = new IMShareContent();
 content.Title = "this is test title";// 标题
 content.Content = "this is test content";// 内容
 content.Link = "http://www.qq.com";// 链接
 content.ImagePath = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg";// 分享的图片地址
 content.ThumbImage = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg";// 缩略图地址
 return content;
 }

/*
 *Type = TEXT_DIALOG
 *Android支持登录渠道：GRN_BT
 */
 private void testGarenaShareTextDialog() {
 IMShareContent content = createDemoShareContent();
 content.ExtraJson = "{\"mediaTagName\":\"your mediaTagName\"}";//mediaTagName
 content.Type = IMShareContent.ShareType.TEXT_DIALOG;
 IMSDKApi.Share.Share(content);
 }
 /*
 *Type = IMAGE_DIALOG
 *Android支持登录渠道：GRN_BT GRN_FB
 *注意：当登录渠道为GRN_Gas时，可以设置shareType=GRN_FB来分享至指定渠道（FB）
 */
 private void testGarenaShareImageDialog() {
 IMShareContent content = createDemoShareContent();
 /*
 *当shareType == "GRN_FB"时Garena-Gas登录时可以指定渠道：Facebook分享
 *不填依照当前登录渠道进行分享
 */
 content.ExtraJson = "{\"mediaTagName\":\"iMSDK_Android_mediaTagName\",\"shareType\":\"GRN_FB\"}";
 content.Type = IMShareContent.ShareType.IMAGE_DIALOG;
 IMSDKApi.Share.Share(content);
 }
 /*
 *Type = LINK_DIALOG
 *Android支持登录渠道：GRN_BT GRN_FB
 *注意：当登录渠道为GRN_Gas时，可以设置shareType=GRN_FB来分享至指定渠道（FB）
 */
 private void testGarenaShareLinkDialog() {
 IMShareContent content = createDemoShareContent();
 /*
 *当shareType == "GRN_FB"时Garena-Gas登录时可以指定渠道：Facebook分享
 *不填依照当前登录渠道进行分享
 */
 content.ExtraJson = "{\"mediaTagName\":\"iMSDK_Android_mediaTagName\",\"caption\":\"iMSDK_Android_caption\",\"shareType\":\"GRN_FB\"}";
 content.Type = IMShareContent.ShareType.LINK_DIALOG;
 IMSDKApi.Share.Share(content);
 }
```

