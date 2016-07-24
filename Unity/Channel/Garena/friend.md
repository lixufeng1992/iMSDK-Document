# Garena好友关系链模块


## 关系链功能支持列表
* <font color=red>Garena提供了静默邀请、分享</font>

| 序号 | 功能 | 是否支持 | 备注 |
|  :--  |  :--  |  :--  |  :--  |
| 1 | 邀请 | √ |- |
| 1 | 分享文本-后台 | √ | - |
| 2 | 分享文本-对话框 | √ | - |
| 3 | 分享链接-后台 | x | - |
| 4 | 分享链接-对话框 | √ | - |
| 5 | 分享图片-后台 | x | - |
| 6 | 分享图片-对话框 | √ | - |

## 字段填写规则

| 分享类型 | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson） |
|  :--  |  :--  |  :--  |  :--  |  :--  |  :--  | :-- |
| 邀请 | - | √ | √ | √ | √ | - |
| 文本（后台） | √ | √ | √ | √ | √ | √ |
| 文本（对话框）| √ | √ | √ | √ | √ | √ |
| 链接（后台） | √ | √ | √ | √（网络链接） | - | √ |
| 链接（对话框） | √ | √ | √ | √（网络链接） | - | √ |
| 图片（后台） | - | - | - | √（本地路径）| - | √ |
| 图片（对话框） | - | - | - | √（本地路径）| - | √ |

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
 android:value="49c1b7af60b1f5557005d101f1f8aa6e0a185c286ee630612ecc2c54c7ac7b27" />
 <meta-data
 android:name="com.garena.sdk.applicationId"
 android:value="100050" />
 <meta-data
 android:name="com.garena.sdk.ApplicationSourceId"
 android:value="2" />
 <!-- application id must be filled to use garena service. many APIs depend on this id, please contact garena mobile game team to get this id -->
 <meta-data
 android:name="com.garena.sdk.applicationId"
 android:value="100050" />
 <!-- same as application id. need to specify for push notification service to work -->
 <meta-data
 android:name="com.garena.sdk.push.applicationId"
 android:value="100050" />
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
 android:authorities="com.facebook.app.FacebookContentProvider940076299433432"
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

##代码示例
```cs
 /*
 * 登录渠道说明：
 * GRN_BT：Garena-Beetalk子渠道
 * GRN_Gas:Garena-Garena子渠道
 * GRN_FB:Garena-Facebook子渠道
 * GRN_GU:Garena-Guest子渠道
 */

void Start() {
 IMSDKApi.Friend.Initialize ();
 IMSDKApi.Friend.SetChannel("Garena");
}

void TestGetFriendsCallback(IMFriendResult result) {
 if(result.RetCode == 1) {
 Debug.Log("get friend ok");

 foreach(IMFriendInfo item in result.FriendInfoList) {
 Debug.Log("get friend : " + item.OpenId);
 }
 }
 else {
 Debug.Log("get friend error : " + result.ErrorMsg);
 }
}

void TestGetFriends() {
 IMSDKApi.Friend.GetFriends(1, 100, TestGetFriendsCallback);
}

void TestFriendCallback(IMFriendResult result) {
 if(result.RetCode == 1) {
 Debug.Log("message ok "");
 }
 else {
 Debug.Log("message error : " + result.ErrorMsg);
 }
}

/*
 *支持登录渠道：GRN_FB
 */
void TestInvite() {
 IMFriendContent content = new IMFriendContent();
 content.Title = "this is title";
 content.Content = "this is content";
 content.Link = "http://ieg.qq.com";
 content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
 content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";

 IMSDKApi.Friend.Invite(content, TestFriendCallback);
}

void TestFriend() {
 testGarenaFriendText();//Text 静默邀请
 testGarenaFriendTextDialog();//TextDialog
 testGarenaFriendLinkDialog();//LinkDialog
 testGarenaFriendImageDialog();//ImageDialog
}

 private IMFriendContent createDemoFriendContent(){
 IMFriendContent content = new IMFriendContent();
 content.Title = "this is test title";// 标题
 content.Content = "this is test content";// 内容
 content.Link = "http://www.qq.com";// 链接
 content.ImagePath = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg";// 分享的图片地址
 content.ThumbImage = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg";// 缩略图地址
 return content;
 }

 /*
 *garena提供静默邀请
 *Type = TEXT
 *Android支持登录渠道：GRN_Gas GRN_BT
 */
 private void testGarenaFriendText() {
 IMFriendContent content = createDemoFriendContent();
 content.User = "user1,user2,user3...";//邀请的好友，以","分隔
 content.ExtraJson = "{\"fbObjectId\":\"your fbObjectId\"}";//你配置的fb的ObjectId
 content.Type = IMFriendContent.MessageType.TEXT;
 IMSDKApi.Friend.SendMessage(content, TestFriendCallback);
 }

 /*
 *Type = TEXT_DIALOG
 *Android支持登录渠道：GRN_Gas GRN_BT
 */
 private void testGarenaFriendTextDialog() {
 IMFriendContent content = createDemoFriendContent();
 content.ExtraJson = "{\"mediaTagName\":\"your mediaTagName\"}";//mediaTagName
 content.Type = IMFriendContent.MessageType.TEXT_DIALOG;
 IMSDKApi.Friend.SendMessage(content, TestFriendCallback);
 }

 /*
 *Type = IMAGE_DIALOG
 *Android支持登录渠道：GRN_Gas GRN_BT
 */
 private void testGarenaFriendImageDialog() {
 IMFriendContent content = createDemoFriendContent();
 content.ExtraJson = "{\"mediaTagName\":\"your mediaTagName\"}";//mediaTagName
 content.Type = IMFriendContent.MessageType.IMAGE_DIALOG;
 IMSDKApi.Friend.SendMessage(content, TestFriendCallback);
 }

 /*
 *Type = IMAGE_DIALOG
 *Android支持登录渠道：GRN_Gas GRN_BT
 */
 private void testGarenaFriendLinkDialog() {
 IMFriendContent content = createDemoFriendContent();
 content.ExtraJson = "{\"mediaTagName\":\"your mediaTagName\",\"caption\":\"your caption\"}";//caption
 content.Type = IMFriendContent.MessageType.LINK_DIALOG;
 IMSDKApi.Friend.SendMessage(content, TestFriendCallback);
 }
```


