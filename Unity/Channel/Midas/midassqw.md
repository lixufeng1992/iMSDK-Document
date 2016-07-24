##  4.5.5.13 SQW 工程配置

###  SQW 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  SQW 权限配置，在AndroidManifest.xml中新增一下权限

```xml
 <uses-permission android:name="android.permission.INTERNET"/>
 <uses-permission android:name="android.permission.WAKE_LOCK" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 <uses-permission android:name="com.android.vending.CHECK_LICENSE" />
 <uses-permission android:name="com.android.vending.BILLING" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
 <uses-permission android:name="android.permission.USE_CREDENTIALS" />
<!-- sqw start -->
 <activity
     android:name="com.game37.sdk.ui.SDKLoginActivity"
     android:label="@string/app_name"
     android:screenOrientation="landscape"
     android:theme="@android:style/Theme.Translucent.NoTitleBar"
     android:windowSoftInputMode="stateAlwaysHidden" >
 </activity>
 <activity
     android:name="com.chartboost.sdk.CBImpressionActivity"
     android:excludeFromRecents="true"
     android:hardwareAccelerated="true"
     android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"
     android:configChanges="keyboardHidden|orientation|screenSize" />
 <receiver
     android:name="com.appsflyer.MultipleInstallBroadcastReceiver"
     android:exported="true" >
 <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>
 <receiver
     android:name="com.ujoy.sdk.utils.UjoyBroadcastReceiver"
     android:exported="true" >
 <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>
 <receiver android:name="com.appsflyer.AppsFlyerLib">
 <intent-filter>
     <action android:name="android.intent.action.PACKAGE_REMOVED"/>
     <data android:scheme="package"/>
 </intent-filter>
 </receiver>
 <!-- sqw end -->

 ```



###  SQW 代码实例

* 与[米大师支付](../../Module/pay-midas.md) 一致
