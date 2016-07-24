## 6.4.1 Toy(Android) 工程配置

### Android工程通用配置

* Toy在AndroidManifest.xml中配置如下
 ```xml
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
 <meta-data 
    android:name="TwitterConsumerKey" android:value="IUREkFCuKCnnE97WRAnSOVpDi" />
 <meta-data 
    android:name="TwitterConsumerSecret"         android:value="La104NxpSHgs98qq66qxSMMBPg51QAaX4FOGJMr4dJUfQXOjx8" />
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
 <!--如提示SignInHubActivity丢失，打开注释-->
 <!--<activity
     android:name="com.google.android.gms.auth.api.signin.internal.SignInHubActivity"
     android:screenOrientation="portrait"
     android:windowSoftInputMode="stateAlwaysHidden|adjustPan" />-->
 </application>
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.USE_CREDENTIALS" />
 <uses-permission android:name="android.permission.GET_TASKS" />
 <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
 ```