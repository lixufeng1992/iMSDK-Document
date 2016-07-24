##  4.5.5.10 MidasPW 工程配置

###  MidasPW 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasPW 权限配置，在AndroidManifest.xml中新增一下权限

```xml
 <!--通用权限-->
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 <application>
 <!-- midas paymentwall start -->
 <!--通用 Activity-->
 <activity
     android:name="com.tencent.midas.oversea.business.APMallActivity"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:screenOrientation="landscape"
     android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
 </activity>
 <activity
     android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:screenOrientation="landscape"
     android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>
 <!--Paymentwall Activity-->
 <activity
     android:name="com.paymentwall.sdk.pwlocal.ui.PwLocalActivity"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:screenOrientation="landscape"
     android:theme="@android:style/Theme.Translucent" />
 <!-- midas paymentwall end -->
 </application>

 ```



###  MidasPW 代码实例

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