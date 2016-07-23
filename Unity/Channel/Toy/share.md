# Toy分享模块


## 分享功能支持列表
* <font color=red>请注意分享功能中部分渠道没有回调</font>
*
| 序号 | 功能 | 是否支持 | 备注 |
| :--: | :--: | :----: | :--: |
| 1 | 分享文本-后台 | x |- |
| 2 | 分享文本-对话框 | √ | - |
| 3 | 分享链接-后台 | x | - |
| 4 | 分享链接-对话框 | √ | - |
| 5 | 分享图片-后台 | x | - |
| 6 | 分享图片-对话框 | √ | - |

## 字段填写规则

| 分享类型 | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson） |
| :--: | :--: | :--: | :--: | :--: | :--: | -- |
| 文本（后台） | - | - | - | - | - | - |
| 文本（对话框） | √ | √ | √ | √ | √ | √ |
| 链接（后台） | - | - | - | - | - | - |
| 链接（对话框） | √ | √ | √ | √ | √ | √ |
| 图片（后台） | - | - | - | - | - | - |
| 图片（对话框） | √ | √ | √ | √ | √ | √ |

## 工程配置

### Android工程配置

 ```xml
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
 <meta-data android:name="TwitterConsumerSecret" android:value="La104NxpSHgs98qq66qxSMMBPg51QAaX4FOGJMr4dJUfQXOjx8" />
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

 按Toy工程通用配置进行配置即可

 ##代码示例
 ```cs
 void Start() {
 IMSDKApi.Share.Initialize ();
 IMSDKApi.Share.SetChannel("Toy");
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
 testToyShareTextDialog();//分享TextDialog
 testToyShareLinkDialog();//分享LinkDialog
 testToyShareImageDialog();//分享ImageDialog
}

 private IMShareContent createDemoShareContent(){
 IMShareContent content = new IMShareContent();
 content.title = "this is test title";// 标题
 content.content = "this is test content";// 内容
 content.link = "http://www.qq.com";// 链接
 content.imagePath = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg";// 分享的图片地址
 content.ThumbImage = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg";// 缩略图地址
 return content;
 }

 /*
 *Toy的ShareTextDialog是没有回调的
 */
 private void testToyShareTextDialog() {
 IMShareContent content = createDemoShareContent();
 content.type = MessageType.TEXT_DIALOG;
 IMSDKApi.Share.share(content);
 }

 /*
 *1.当ExtraJson值ShareLine为Yes时，Line分享(没有回调)
 *2.否则当当前登录渠道为Toy-Facebook时，Facebook分享
 *3.否则当当前登录渠道为Toy-Twitter时，Twitter分享(没有回调)
 */
 private void testToyShareImageDialog() {
 IMShareContent content = createDemoShareContent();
 /*
 *Line分享时才需填写ExtraJson，其余渠道的分享可以不填。
 */
 content.ExtraJson = "{\"ShareLine\":\"yes\"}";
 content.type = MessageType.IMAGE_DIALOG;
 IMSDKApi.Share.share(content);
 }

 /*
 *Toy的ShareLinkDialog只支持当前登录渠道为Toy-Facebook时
 *其余登录渠道不支持
 */
 private void testToyShareLinkDialog() {
 IMShareContent content = createDemoShareContent();
 content.type = MessageType.LINK_DIALOG;
 IMSDKApi.Share.share(content);
 }
 ```
