##  MidasFortumo 工程配置

###  MidasFortumo配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

* MidasFortumo权限配置，在AndroidManifest.xml中新增一下权限

 ```xml
 <!--通用权限-->
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

 <!--Fortumo支付需要的权限-->
 <uses-permission android:name="android.permission.RECEIVE_SMS" />
 <uses-permission android:name="android.permission.SEND_SMS" />
 <!--Fortumo支付自定义权限，XXXX部分请定义为您自己的包名
 从Android L开始，signature的自定义权限需要签名相同。
 <permission android:name="XXXX.permission.PAYMENT_BROADCAST_PERMISSION" --> 
 <permission android:name="[your_package_name].permission.PAYMENT_BROADCAST_PERMISSION"
     android:label="Read payment status"
     android:protectionLevel="signature" />
 <!-- "signature" permission granted automatically by system, without notifying user. -->
 <uses-permission android:name="[your_package_name].permission.PAYMENT_BROADCAST_PERMISSION" />
 ```

* MidasFortumo Activity 配置，在Application节点中添加如下activity配置

 ```xml
 <!-- midas fortumo start -->
 <!--midas通用Activity-->
 <activity
     android:name="com.tencent.midas.oversea.business.APMallActivity"
     android:screenOrientation="sensorLandscape"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
 </activity>
 <activity
     android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
     android:screenOrientation="sensorLandscape"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>

 <!--Fortumo专用-->
 <activity
     android:name="com.tencent.midas.oversea.business.payhub.fortumo.APProxyActivity"
     android:screenOrientation="sensorLandscape"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>
 <receiver android:name="mp.MpSMSReceiver">
 <intent-filter>
     <action android:name="android.provider.Telephony.SMS_RECEIVED" />
 </intent-filter>
 </receiver>
 <service android:name="mp.MpService" />
 <service android:name="mp.StatusUpdateService" />
 <activity android:name="mp.MpActivity"
     android:theme="@android:style/Theme.Translucent.NoTitleBar"
     android:configChanges="orientation|keyboardHidden|screenSize" />
 <!-- 实现自己的广播类来监听Fortumo的支付状态,需要 "signature" permission -->
 <receiver android:name="com.tencent.imsdk.pay.midasfortumo.FortumoPaymentStatusReceiver"
     android:permission="com.tencent.midas.oversea.permission.PAYMENT_BROADCAST_PERMISSION">
 <intent-filter>
     <action android:name="mp.info.PAYMENT_STATUS_CHANGED" />
 </intent-filter>
 </receiver>
 <!-- midas fortumo end -->
 ```

### MidasFortumo代码实例

* 与[米大师支付](../../Module/pay-midas.md)文档大致一致， 在入参时有细微差别   

<font color=red>* 以下为细微差别部分</font>
```cs
/*
 *差别部分：
 *fortumo不需要物品，所以ProductId传为空
 */
 content.ProductId = "";
```


```cs
/*
*Android-Midas 初始化
*/
IMSDKApi.Pay.Initialize(androidGooglePublicKey);

IMSDKApi.Pay.SetChannel("MidasFortumo");
IMSDKApi.Pay.SetEnv("test");//目前暂时只支持test环境
IMSDKApi.Pay.EnableDebugLog(true);
IMSDKApi.Pay.SetIDC("local");

/*
*构造Android：IMMidasPayContent
*/
IMMidasPayContent GetMidasAndroidPayContent() {
 IMMidasPayContent content = new IMMidasPayContent ();
 content.OfferId = "1450003696";
 content.OpenId = openId;
 content.OpenKey = accessToken;
 content.SessionId = "hy_gameid"; // usually "hy_gameid"
 //content.SessionType = "st_overseas"; // check imsdk login status
 content.SessionType = "st_dummy"; // do NOT check imsdk login status
 content.ZoneId = "1";
 content.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
 content.PfKey = "pfKey";
 content.ProductId = "";//fortumo为空
 content.ResId = "unipay_abroad_iconload";
 content.Country = "US";
 content.CurrencyType = "USD";
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

