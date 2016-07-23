## 6.4.2.10 MidasZalo 工程配置

###  MidasZalo 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasZalo 权限配置，在AndroidManifest.xml中新增一下权限

```xml
  <permission
 android:name="com.vng.vuapk.permission.C2D_MESSAGE"
 android:protectionLevel="signature" />
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
 <uses-permission android:name="com.vng.vuapk.permission.C2D_MESSAGE" />
 <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.WAKE_LOCK" />
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 <uses-permission android:name="android.permission.CAMERA" />
 <uses-feature android:name="android.hardware.camera" />
 <uses-permission android:name="com.android.vending.BILLING" />
 <uses-feature android:name="android.hardware.camera.autofocus" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.USE_CREDENTIALS" />
 <uses-permission android:name="com.zing.zalo.permission.ACCESS_THIRD_PARTY_APP_AUTHORIZATION" />
 <uses-permission android:name="android.permission.INTERNET" />
 <!-- zalo end -->
 <!-- application必须继承"com.zing.zalo.zalosdk.oauth.ZaloSDKApplication" -->
 <application
 android:name="com.zing.zalo.zalosdk.oauth.ZaloSDKApplication"
 android:allowBackup="false"
 android:icon="@drawable/ic_launcher"
 android:label="@string/app_name" >
 <!-- zalo start -->
 <activity
 android:name="com.android.m6.guestlogin.ui.LoginActivity"
 android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
 android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
 </activity>
 <activity
 android:name="com.zing.zalo.zalosdk.payment.direct.PaymentGatewayActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:theme="@android:style/Theme.Translucent.NoTitleBar" >
 </activity>
 <activity
 android:name="com.zing.zalo.zalosdk.payment.direct.PaymentChannelActivity"
 android:configChanges="orientation|keyboardHidden|screenSize"
 android:launchMode="singleTop"
 android:theme="@android:style/Theme.Translucent.NoTitleBar"
 android:windowSoftInputMode="stateHidden|stateAlwaysHidden" >
 </activity>
 <activity
 android:name="com.zing.zalo.zalosdk.payment.direct.CameraActivity"
 android:configChanges="keyboardHidden|screenSize|orientation"
 android:launchMode="singleTop"
 android:theme="@android:style/Theme.Black.NoTitleBar.Fullscreen" >
 </activity>
 <activity
 android:name="com.zing.zalo.zalosdk.payment.direct.ReviewActivity"
 android:configChanges="keyboardHidden|screenSize|orientation"
 android:launchMode="singleTop"
 android:theme="@android:style/Theme.Translucent.NoTitleBar" >
 </activity>
 <activity
 android:name="com.android.m6.guestlogin.ui.PaymentChosen"
 android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
 android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
 </activity>
 <receiver
 android:name="com.vng.mb.sdk.push.GcmBroadcastReceiver"
 android:permission="com.google.android.c2dm.permission.SEND" >
 <intent-filter>
 <action android:name="com.google.android.c2dm.intent.RECEIVE" />
 <category android:name="com.vng.mb.sdk.sample" />
 </intent-filter>
 </receiver>
 <service android:name="com.vng.mb.sdk.push.GCMNotificationIntentService" />
 <receiver
 android:name="com.google.ads.conversiontracking.InstallReceiver"
 android:exported="true" >
 <intent-filter>
 <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>
 <meta-data
 android:name="com.tencent.imsdk.zaloAppSecretKey"
 android:value="\ CdBqScADr9ceM6f6JEqD" />
 <meta-data
 android:name="appID"
 android:value="\ 4384741679245596449" />
 <meta-data
 android:name="configOffSuccessDialog"
 android:value="true" />
 <meta-data
 android:name="configFullScreen"
 android:value="true" />
 <meta-data
 android:name="configLoginChannel"
 android:value="0" />
 <meta-data
 android:name="sender_id"
 android:value="\ 146406334780" />
 <!-- 39608353167 146406334780 -->
 <meta-data
 android:name="conversion_id"
 android:value="" />
 <meta-data
 android:name="mto_label"
 android:value="" />
 <!-- zalo end -->
 <!-- Midas通用Activity start -->
 <activity
 android:name="com.tencent.midas.oversea.business.APMallActivity"
 android:configChanges="keyboard|keyboardHidden"
 android:screenOrientation="landscape"
 android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
 </activity>
 <activity
 android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
 android:configChanges="keyboard|keyboardHidden"
 android:screenOrientation="landscape"
 android:theme="@android:style/Theme.Translucent.NoTitleBar" >
 </activity>
 <!-- Midas通用Activity end -->
 <!-- google pay start -->
 <meta-data
 android:name="com.google.android.gms.version"
 android:value="7571000" />
 <!-- google pay end -->
 <!-- facebook start -->
 <meta-data
 android:name="com.facebook.sdk.ApplicationId"
 android:value="\ 1438793016430189" />
 <activity
 android:name="com.facebook.FacebookActivity"
 android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
 android:label="@string/app_name"
 android:theme="@android:style/Theme.Translucent.NoTitleBar" />
 <activity
 android:name="com.facebook.LoginActivity"
 android:label="fb login" >
 </activity>
 <!-- facebook end -->
 </application>

 ```



###  MidasZalo 代码实例

* 与[米大师支付](../../Module/pay-midas.md) 一致

```cs
/*
*Android-Midas 初始化
*/
IMSDKApi.Pay.Initialize(androidGooglePublicKey);
//iOS-Midas支付无需初始化
IMSDKApi.Pay.SetChannel("MidasPW");
IMSDKApi.Pay.SetEnv("test");//目前暂时只支持test环境
IMSDKApi.Pay.EnableDebugLog(true);
IMSDKApi.Pay.SetIDC("local");
/*
*构造Android：IMMidasPayContent 该结构体适用于iOS-Midas支付&Android-Midas支付
*/
IMMidasPayContent GetMidasAndroidPayContent() {
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
 content.ProductId = "paymentwall_p1";
 content.ResId = "unipay_abroad_iconload";
 content.Country = "US";
 content.CurrencyType = "USD";
 content.BuyGameOrGoodsOrMonth = "Game";//Game:钻石 Goods:道具 Month:月卡
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

```