## 6.4.2.9 MidasPW 工程配置

###  MidasPW 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasPW 权限配置，在AndroidManifest.xml中新增一下权限

```xml
 <!--通用权限--> <uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<!--MOL支付需要的权限-->
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
<uses-permission android:name="android.permission.WRITE_SETTINGS" />
<uses-permission android:name="com.android.launcher.permission.READ_SETTINGS" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.SEND_SMS"/>

<!--通用Activity-->
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
<!--MOL Activity 无-->

 ```



###  MidasPW 代码实例

* 与[米大师支付](../../Module/pay-midas.md) 大致一致，在入参时有细微差别
以下为细微差别部分
```cs
/*
 *差别部分：
 *payChannel值为：mol_pin时，开启MOL 点卡支付
 *payChannel值为：mol_hf时，开启MOL 话费支付
 *payChannel值为：mol_acct时，开启MOL 账户支付
 */
 content.payChannel = "mol_pin";
```

```cs
/*
*Android-Midas 初始化
*/
IMSDKApi.Pay.Initialize(androidGooglePublicKey);
//iOS-Midas支付无需初始化

IMSDKApi.Pay.SetChannel("MidasMOL");
IMSDKApi.Pay.SetEnv("test");//目前暂时只支持test环境
IMSDKApi.Pay.EnableDebugLog(true);
IMSDKApi.Pay.SetIDC("local");

/*
*构造Android：IMMidasPayContent
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
 content.ProductId = "midas_product_1";
 content.ResId = "unipay_abroad_iconload";
 content.Country = "US";
 content.CurrencyType = "USD";
 info.payChannel = "mol_pin";//"mol_pin:点卡","mol_hf：话费","mol_acct：账户"
 content.BuyGameOrGoodsOrMonth = "Game";//Game:钻石 Goods:道具 Month:月卡
 return content;
 }
/*
*构造iOS：IMMidasPayContent
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
*构造IMPayPrepareContent
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