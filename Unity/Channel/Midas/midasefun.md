## 6.4.2.2 MidasEfun 工程配置

### MidasEfun配置

* MidasGoogle权限配置，在AndroidManifest.xml中新增一下权限

  ```xml
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="com.android.vending.BILLING" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.VIBRATE" />

    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <!-- g+ -->
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.USE_CREDENTIALS" />

    <uses-feature
    android:name="android.hardware.microphone"
    android:required="false" />
    <uses-feature
    android:name="android.hardware.telephony"
    android:required="false" />
    <uses-feature
    android:name="android.hardware.location.gps"
    android:required="false" />
    <uses-feature
    android:name="android.hardware.location"
    android:required="false" />
    <uses-feature
    android:name="android.hardware.location.NETWORK"
    android:required="false" />
  ```

* MidasEfun Activity 配置，在Application节点中添加如下activity配置

```xml
  <activity
     android:name="com.efun.tc.ui.PageContainer"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <activity
     android:name="com.efun.tc.ui.AutoLoginActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <activity
     android:name="com.efun.tc.ui.FacebookActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <activity
     android:name="com.facebook.FacebookActivity"
     android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
     android:screenOrientation="sensorLandscape" />
 <!-- facebook activity声明 -->
 <!-- 邀请 -->
 <activity
     android:name="com.efun.invite.activity.InviteActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <!-- 粉丝页 -->
 <activity
     android:name="com.efun.invite.activity.EfunFansActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <!-- 功能说明 -->
 <activity
     android:name="com.efun.invite.activity.InformaActivity"
     android:configChanges="orientation|keyboardHidden"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>

 <!-- facebook activity声明 -->
 <activity
     android:name="com.facebook.FacebookActivity"
     android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
     android:screenOrientation="sensorLandscape" />

 <!-- facebook功能 -->

 <!-- 分享 -->
 <activity
     android:name="com.efun.facebook.share.activity.EfunFBFunctionActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <activity
     android:name="com.facebook.LoginActivity"
     android:screenOrientation="sensorLandscape" />
     <activity
     android:name="com.efun.invite.activity.EfunFacebookActivity"
     android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="sensorLandscape"
     android:theme="@style/Transparent"
     android:windowSoftInputMode="stateHidden" >
 </activity>

 <!-- 客服 -->
 <activity
     android:name="com.efun.tc.service.EfunCustomerService"
     android:configChanges="orientation|keyboardHidden"
     android:launchMode="singleTask"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <!-- google 储值 -->
 <activity
     android:name="com.efun.tc.google.EfunWebGoogleActivity"
     android:configChanges="orientation|keyboardHidden"
     android:launchMode="singleTask"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>

 <!-- google 储值 -->
 <activity
     android:name="com.efun.tc.google.BillingActivity"
     android:configChanges="orientation|keyboardHidden"
     android:launchMode="singleTask"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateHidden" >
 </activity>
 <!-- 储值服务兑换券-->
 <service android:name="com.efun.googlepay.EfunGooglePayService"></service>

 <!-- appsflyer -->
 <receiver
     android:name="com.appsflyer.MultipleInstallBroadcastReceiver"
     android:exported="true" >
 <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>

 <!-- Google Analytics -->
 <service
     android:name="com.efun.ads.activity.EfunGAService"
     android:exported="false" >
 </service>
 <!-- S2S ads -->
 <service
     android:name="com.efun.ads.activity.EfunAdsS2SService"
     android:exported="false" >
 </service>
 <!-- GA brocast -->
 <receiver
     android:name="com.efun.ads.activity.GABroadcact"
     android:exported="true" >
 <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>
 <!-- AdWords -->
 <receiver
     android:name="com.google.ads.conversiontracking.InstallReceiver"
     android:exported="true" >
 <intent-filter>
 <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>

 <meta-data
     android:name="com.facebook.sdk.ApplicationId"
     android:value="@string/efunFBApplicationId" />
 <meta-data
     android:name="com.facebook.sdk.ApplicationName"
     android:value="@string/facebook_app_name" />
 <meta-data
     android:name="com.google.android.gms.version"
     android:value="@integer/google_play_services_version" />

 <!-- 平台 -->
 <!-- 平台主类 -->
 <activity
     android:name="com.efun.platform.FrameTabContainer"
     android:configChanges="keyboardHidden|orientation"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 普通的webView頁面类 -->
 <activity
     android:name="com.efun.platform.module.WebActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 游戲詳情类 -->
 <activity
     android:name="com.efun.platform.module.game.activity.GameDetailActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 游戲評論頁面 -->
 <activity
     android:name="com.efun.platform.module.game.activity.GameCommendActivity"
     android:theme="@style/Transparent"
     android:windowSoftInputMode="stateVisible|adjustPan" >
 </activity>
 <!-- 禮包列表 -->
 <activity
     android:name="com.efun.platform.module.welfare.activity.GiftListActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 2.0.7.6增加新闻 -->
 <activity
     android:name="com.efun.platform.module.summary.activity.SummaryListActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 活動列表 -->
 <activity
     android:name="com.efun.platform.module.welfare.activity.ActListActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 我的序號中心 -->
 <activity
     android:name="com.efun.platform.module.welfare.activity.GiftSelfActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 禮包詳情 -->
 <activity
     android:name="com.efun.platform.module.welfare.activity.GiftDetailActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- -->
 <activity
     android:name="com.efun.platform.module.summary.activity.SummaryListActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 活動詳情 -->
 <!-- <activity
     android:name="com.efun.platform.module.welfare.activity.ActDetailActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity> -->
 <!-- 玩家提問 -->
 <activity
     android:name="com.efun.platform.module.cs.activity.CsAskActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar"
     android:windowSoftInputMode="stateHidden|adjustPan" >
 </activity>
 <!-- 客服問題 -->
 <activity
     android:name="com.efun.platform.module.cs.activity.CsQuestionActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 常見問題 -->
 <activity
     android:name="com.efun.platform.module.cs.activity.CsQuestionContentActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 客服回復 -->
 <activity
     android:name="com.efun.platform.module.cs.activity.CsReplyActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar"
     android:windowSoftInputMode="stateHidden|adjustPan" >
 </activity>
 <!-- 玩家回復 -->
 <activity
     android:name="com.efun.platform.module.cs.activity.CsCommendActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@style/Transparent"
     android:windowSoftInputMode="stateVisible|adjustPan" >
 </activity>
 <!-- 客服回復詳情 -->
 <activity
     android:name="com.efun.platform.module.cs.activity.CsReplyDetailsActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Light.NoTitleBar"
     android:windowSoftInputMode="stateVisible|stateHidden" >
 </activity>
 <!-- 綁定手機號 -->
 <activity
     android:name="com.efun.platform.module.account.activity.BindPhoneActivity"
     android:theme="@android:style/Theme.Light.NoTitleBar" >
 </activity>
 <!-- 限时活动 （2.0.3版添加） -->
 <activity
     android:name="com.efun.platform.module.activity.LimitedWebActivity"
     android:configChanges="keyboardHidden|orientation|screenSize"
     android:theme="@style/Transparent" >
 </activity>
 <!-- 平台 -->

 <meta-data android:name="com.tencent.imsdk.efun.GameCode" android:value="twqmcs" />

 <activity
     android:name="com.tencent.midas.oversea.business.APMallActivity"
     android:screenOrientation="portrait"
     android:configChanges="keyboard|keyboardHidden|screenSize|orientation"
     android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
 </activity>
 <activity
     android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
     android:screenOrientation="portrait"
     android:configChanges="keyboard|keyboardHidden|screenSize|orientation"
     android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>
    ```
  
### MidasEfun代码实例

<font color=red>* 以下为细微差别部分</font>
```cs
/*
 *差别部分：
 *payChannel值为：os_efun时，开启Efun谷歌支付
 *payChannel值为：os_efunwap，开启Efun普通支付
 */
 content.payChannel = "os_efun";

 /*
 *需要游戏拼凑该字符串
 *roleId值
 *roleName值
 *roleLevel值
 *serverId值
 */
 content.Extras = "roleId=aaaa&roleName=bbbb&roleLevel=cccc&serverId=1";
```


```cs
/*
*Android-Midas 初始化
*/
IMSDKApi.Pay.Initialize(androidGooglePublicKey);
//iOS-Midas支付无需初始化

IMSDKApi.Pay.SetChannel("MidasEfun");
IMSDKApi.Pay.SetEnv("dev");//目前暂时只支持dev环境
IMSDKApi.Pay.EnableDebugLog(true);
IMSDKApi.Pay.SetIDC("local");

/*
*构造Android：IMMidasPayContent 该结构体适用于iOS-Midas支付&Android-Midas支付
*/
IMMidasPayContent GetMidasAndroidPayContent() {
 IMMidasPayContent content = new IMMidasPayContent ();
 content.OfferId = "1450007160";
 content.OpenId = openId;
 content.OpenKey = accessToken;
 content.SessionId = "hy_gameid"; // usually "hy_gameid"
 //content.SessionType = "st_overseas"; // check imsdk login status
 content.SessionType = "st_dummy"; // do NOT check imsdk login status
 content.ZoneId = "1";
 content.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
 content.PfKey = "pfKey";
 content.ProductId = "tw.qmcs.100usd";
 content.ResId = "unipay_abroad_iconload";
 content.Country = "US";
 content.CurrencyType = "USD";
 content.BuyGameOrGoodsOrMonth = "Game";//Game:钻石 Goods:道具 Month:月卡

 /*
 *payChannel值为：os_efun时，开启Efun谷歌支付
 *payChannel值为：os_efunwap，开启Efun普通支付
 */
 content.payChannel = "os_efun";
 content.Extras = "roleId=aaaa&roleName=bbbb&roleLevel=cccc&serverId=1";
 return content;
 }
/*
*构造iOS：IMMidasPayContent 该结构体适用于iOS-Midas支付&Android-Midas支付
*请注意在构造Android和iOS时的细微差别
*/
IMMidasPayContent GetMidasIOSPayContent() {
 IMMidasPayContent content = new IMMidasPayContent ();
 content.OfferId = "1450005285";
 content.OpenId = openId;
 content.OpenKey = accessToken;
 content.SessionId = "hy_gameid"; // usually "hy_gameid"
 //content.SessionType = "st_overseas"; // check imsdk login status
 content.SessionType = "st_dummy"; // do NOT check imsdk login status
 content.ZoneId = "1";
 content.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
 content.PfKey = "pfKey";
 content.ProductId = "midas_product_1";
 content.ResId = "unipay_abroad_iconload";
 content.Country = "CN";
 return content;
 }
/*
*构造IMPayPrepareContent 该结构体适用于iOS-Midas支付&Android-Midas支付
*/
IMPayPrepareContent prepareContent = new IMPayPrepareContent();
prepareContent.AppId = GetMidasAndroidPayContent().OfferId;
prepareContent.OpenId = GetMidasAndroidPayContent().OpenId;
prepareContent.OpenKey = GetMidasAndroidPayContent().OpenKey;
prepareContent.SessionId = GetMidasAndroidPayContent().SessionId;
prepareContent.SessionType = GetMidasAndroidPayContent().SessionType;
prepareContent.Pf = GetMidasAndroidPayContent().Pf;
prepareContent.PfKey = GetMidasAndroidPayContent().PfKey;
prepareContent.ZoneId = GetMidasAndroidPayContent().ZoneId;

IMSDKApi.Pay.Prepare(prepareContent);


/*
*Pay:支付
*/
IMSDKApi.Pay.Pay(GetMidasAndroidPayContent(),MidasPayCallback);

/*
*efun暂时不支持 获取营销活动、获取商品信息功能
*/
 ```
