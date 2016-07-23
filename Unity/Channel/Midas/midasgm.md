## 6.4.2.12 MidasGM工程配置

###  MidasGM 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasGM 权限配置，在AndroidManifest.xml中新增一下权限

```xml
 <uses-permission android:name="android.permission.INTERNET"/>
 <uses-permission android:name="android.permission.WAKE_LOCK" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 <uses-permission android:name="android.permission.GET_TASKS" />
 <uses-permission android:name="com.android.vending.CHECK_LICENSE" />
 <uses-permission android:name="com.android.vending.BILLING" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
 <uses-permission android:name="android.permission.USE_CREDENTIALS" />
<activity
     android:name="com.ujoy.sdk.ui.EntranceActivity"
     android:label="@string/app_name"
     android:windowSoftInputMode="stateAlwaysHidden" >
 </activity>
 <activity
     android:name="com.ujoy.sdk.ui.FriendListActivityFragment"
     android:configChanges="orientation"
     android:label="@string/app_name"
     android:theme="@android:style/Theme.Translucent.NoTitleBar"
     android:windowSoftInputMode="stateAlwaysHidden" >
 </activity>
 <activity
     android:name="com.ujoy.sdk.ui.InteractionActivity"
     android:label="@string/app_name"
     android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"
     android:screenOrientation="sensorLandscape"
     android:windowSoftInputMode="stateAlwaysHidden" >
 </activity>
 <activity
     android:name="com.ujoy.sdk.ui.AwardActivity"
     android:configChanges="orientation"
     android:label="@string/app_name"
     android:theme="@android:style/Theme.Light.NoTitleBar"
     android:windowSoftInputMode="stateAlwaysHidden" >
 </activity>
 <activity
     android:name="com.facebook.LoginActivity"
     android:label="@string/app_name"
     android:theme="@android:style/Theme.Translucent.NoTitleBar" >
 </activity>
 <activity
     android:name="com.facebook.FacebookActivity"
     android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
     android:label="@string/app_name"
     android:theme="@android:style/Theme.Translucent.NoTitleBar" />
 <meta-data
     android:name="com.facebook.sdk.ApplicationId"
     android:value="\ 473451279499510" />
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
 <meta-data
     android:name="com.google.android.gms.version"
     android:value="7571000" />
 <receiver android:name="com.appsflyer.AppsFlyerLib">
 <intent-filter>
     <action android:name="android.intent.action.PACKAGE_REMOVED"/>
     <data android:scheme="package"/>
 </intent-filter>
 </receiver>
 <service android:name="com.ujoy.sdk.push.GCMIntentService" />
 <service android:name="com.ujoy.sdk.utils.MQService"
     android:permission="android.permission.INTERNET">
 <intent-filter >
 <category android:name="android.intent.category.DEFAULT"/>
     <action android:name="com.gm99.kof.mqservice"/>
 </intent-filter>
 </service>
 <meta-data
     android:name="com.google.android.gms.version"
     android:value="7571000" />
 <!-- Activity start -->
 <activity
     android:name="com.tencent.midas.oversea.business.APMallActivity"
     android:configChanges="keyboard|keyboardHidden"
     android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
 </activity>
 <activity
     android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Translucent.NoTitleBar" >
 </activity>
 <!-- Activity end -->
 ```



###  MidasGM 代码实例

* 与[米大师支付](../../Module/pay-midas.md) 一致
