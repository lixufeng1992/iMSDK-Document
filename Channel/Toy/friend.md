# Toy好友关系链模块

## 关系链功能支持列表
* <font color=red>Toy关系链目前仅支持邀请接口</font>

| 序号 | 功能 | 是否支持 | 备注 |
| :-- | :-- | :---- | :-- |
| 1 | 邀请 | √ |- |
| 1 | 分享文本-后台 | x | - |
| 2 | 分享文本-对话框 | x | - |
| 3 | 分享链接-后台 | x | - |
| 4 | 分享链接-对话框 | x | - |
| 5 | 分享图片-后台 | x | - |
| 6 | 分享图片-对话框 | x | - |

## 字段填写规则

| 分享类型 | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson） |
| :-- | :-- | :-- | :-- | :-- | :-- |  :-- |
| 邀请 | - | √ | √ | √ | √ | √ |
| 文本（后台） | √ | √ | √ | √ | √ | √ |
| 文本（对话框）| √ | √ | √ | √ | √ | √ |
| 链接（后台） | √ | √ | √ | √（网络链接） | - | √ |
| 链接（对话框） | √ | √ | √ | √（网络链接） | - | √ |
| 图片（后台） | - | - | - | √（本地路径）| - | √ |
| 图片（对话框） | - | - | - | √（本地路径）| - | √ |

## 工程配置

### Android工程配置

 ```
 <?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
     package="com.tencent.imsdk.toy.login"
     android:versionCode="1"
     android:versionName="1.0" >

 <uses-sdk
     android:minSdkVersion="8"
     android:targetSdkVersion="21" />

 <application
     android:allowBackup="true"
     android:icon="@drawable/ic_launcher"
     android:label="@string/app_name"
 >
 <activity android:name="com.tencent.imsdk.toy.login.ToyLoginProxyActivity"
     android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
     android:theme="@android:style/Theme.Translucent.NoTitleBar"/>
 <meta-data
     android:name="NPAServiceID"
     android:value="NPA_1151" />

 <meta-data android:name="com.facebook.sdk.ApplicationId"
 android:value="\ 423362744481374" />

 <meta-data android:name="TwitterConsumerKey" android:value="IUREkFCuKCnnE97WRAnSOVpDi" />
 <meta-data 
    android:name="TwitterConsumerSecret"    android:value="La104NxpSHgs98qq66qxSMMBPg51QAaX4FOGJMr4dJUfQXOjx8" />
 <meta-data android:name="TwitterCallbackURL" android:value="http://www.qq.com" />

 <meta-data
     android:name="com.google.android.gms.version"
     android:value="@integer/google_play_services_version" />

 <activity
     android:name="com.nexon.android.ui.NPLoginActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.auth.NXToyLoginSelectActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.auth.NXToyTermsActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.auth.NXToyTermViewActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="com.nexon.android.ui.NXJoinUserAuthWebActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="com.nexon.android.ui.NXJoinWebActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="com.nexon.android.ui.NXJoinSelectActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="com.nexon.android.ui.NXUserAuthWebActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.etc.NXToyShareActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.banner.NXToyFullBannerActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="com.nexon.android.ui.NXSearchIDPWActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="com.nexon.android.ui.NPGetNexonSNActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.banner.NXToyEndingBannerActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.board.NXToyNoticeActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.board.NXToyFAQActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.board.NXToyCSActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.board.NXToyForumActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.etc.NXToyCouponActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyCustomerServiceActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyHelpCenterActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.board.NXToyWebActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>

 <activity
     android:name="com.facebook.FacebookActivity"
     android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
     android:label="@string/app_name"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar" />

 <!-- start Email Authentication related -->
 <activity
     android:name="kr.co.nexon.android.sns.ui.NPEmailLoginCheckActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.android.sns.ui.NPEmailLoginActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.android.sns.ui.NPEmailSignUpActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.android.sns.ui.NPEmailResetPasswordActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="adjustResize" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.android.sns.ui.NPEmailResetPasswordSuccessActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.android.sns.ui.NXEmailWebActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.auth.NXToyLoginATypeSelectActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyPlateActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyGameInfoActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyTermsListActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
     android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyUserInfoActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
     <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>

 <!-- end Email Authentication related -->


 <!-- start Data Backup & Restore -->
 <activity
 android:name="kr.co.nexon.toy.android.ui.backup.NXToyDataBackupActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.backup.NXToyDataRestoreActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen"
 android:windowSoftInputMode="adjustResize" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.backup.NXToyDataBackupMessageActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.backup.NXToyDataRestoreMessageActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <!-- end Data Backup & Restore -->

 <activity
 android:name="kr.co.nexon.toy.android.ui.board.NXToyNCSActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.baseplate.NXToyPushNSMSActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>

 <!-- Japan -->
 <activity
 android:name="kr.co.nexon.toy.android.ui.etc.NXToySettlementFundActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.etc.NXToySettlementFundConfirmActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="kr.co.nexon.toy.android.ui.etc.NXToySettlementFundItemConfirmActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@style/ToyTheme.Translucent.NoTitleBar.Fullscreen" >
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 </intent-filter>
 </activity>
 <activity
 android:name="com.google.android.gms.auth.api.signin.internal.SignInHubActivity"
 android:screenOrientation="portrait"
 android:windowSoftInputMode="stateAlwaysHidden|adjustPan" />
 </application>

 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.USE_CREDENTIALS" />
 <uses-permission android:name="android.permission.GET_TASKS" />
 <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />

</manifest>
 ```

### iOS工程配置

 按Garena工程通用配置进行配置即可

 ##代码示例
 ```cs
void Start() {
 IMSDKApi.Friend.Initialize ();
 IMSDKApi.Friend.SetChannel("Toy");
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

void TestInvite() {
 IMFriendContent content = new IMFriendContent();
 content.user = "subID1,subID2,subID3,subID4,subID5,...";
 content.Title = "this is title";
 content.Content = "this is content";
 content.Link = "http://ieg.qq.com";
 content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
 content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";

 /*
 *以下在Toy-Friend中可以不填
 *Toy-Friend的invite接口，只支持Toy-FB，imsdk已默认为Toy-FB,所以"snsType"可以不填，"extraJson"可以不填
 */
 content.ExtraJson = "{\"snsType\":\"101\"}";//当前登录类型 101为efun-facebook
 IMSDKApi.Friend.Invite(content, TestFriendCallback);
}


 ```




