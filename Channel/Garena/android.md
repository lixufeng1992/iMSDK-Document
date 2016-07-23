## 6.4.1 Midas(Android) 工程配置

### Android工程通用配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同,详情见[Midas配置](../midas.md)，

* Midas内核包权限配置，在AndroidManifest.xml中新增一下权限

 ```xml
  <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="com.android.vending.BILLING" />
 <uses-permission android:name="android.permission.READ_LOGS" />
 <uses-permission android:name="android.permission.WAKE_LOCK" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <application
 android:allowBackup="false"
 android:icon="@drawable/ic_launcher"
 android:label="@string/app_name" >
 <meta-data
 android:name="com.tencent.imsdk.garena.Environment"
 android:value="test" /><!-- production -->
 <meta-data
 android:name="com.tencent.imsdk.garena.APP_SDK_KEY"
 android:value="49c1b7af60b1f5557005d101f1f8aa6e0a185c286ee630612ecc2c54c7ac7b27" />
 <meta-data
 android:name="com.garena.sdk.applicationId"
 android:value="100050" />
 <meta-data
 android:name="com.garena.sdk.ApplicationSourceId"
 android:value="2" />
 <!-- application id must be filled to use garena service. many APIs depend on this id, please contact garena mobile game team to get this id -->
 <meta-data
 android:name="com.garena.sdk.applicationId"
 android:value="100050" />
 <!-- same as application id. need to specify for push notification service to work -->
 <meta-data
 android:name="com.garena.sdk.push.applicationId"
 android:value="100050" />
 <meta-data
 android:name="com.beetalklib.ganalytics.report_url"
 android:value="http://122.11.128.69:2205" />
 <!-- Common login entry activity, the orientation must be specified as portrait or landscape, it can't be specified as sensorLanscape -->
 <activity
 android:name="com.beetalk.sdk.BTLoginActivity"
 android:screenOrientation="portrait"
 android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />
 <!-- BeeTalk Login start -->
 <!-- If enable BeeTalk Login, please register this activity -->
 <activity
 android:name="com.beetalk.sdk.BTBeeTalkAuthActivity"
 android:screenOrientation="portrait" />
 <!-- Facebook App ID unique for each game. Please apply a facebook id on facebook website
 -->
 <meta-data
 android:name="com.facebook.sdk.ApplicationId"
 android:value="@string/facebook_app_id" />
 <activity
 android:name="com.facebook.FacebookActivity"
 android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
 android:label="@string/app_name"
 android:theme="@android:style/Theme.Translucent.NoTitleBar" />
 <provider
 android:name="com.facebook.FacebookContentProvider"
 android:authorities="com.facebook.app.FacebookContentProvider940076299433432"
 android:exported="true" />
 <!-- Facebook Login end -->
 <!-- Garena Login start -->
 <activity
 android:name="com.beetalk.sdk.GarenaAuthActivity"
 android:screenOrientation="portrait" />
 <!-- Garena Login end -->
 <activity
 android:name="com.beetalk.sdk.plugin.GGPluginActivity"
 android:configChanges="orientation|screenSize"
 android:screenOrientation="portrait"
 android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />
 <!-- Garena Payment Start -->
 <activity
 android:name="com.garena.pay.android.GGPayActivity"
 android:configChanges="orientation"
 android:exported="true"
 android:launchMode="singleTop"
 android:screenOrientation="portrait"
 android:theme="@style/Theme.Transparent" />
 <!-- Garena Payment End -->
 <receiver
 android:name="com.garena.android.gpns.logic.AlarmReceiver"
 android:process="com.garena.msdk.pushservice2" >
 <intent-filter>
 <action android:name="com.garena.android.gpns.ALARM_ACTION100050" />
 </intent-filter>
 </receiver>
 <service
 android:name="com.garena.android.gpns.GNotificationService"
 android:enabled="true"
 android:exported="true"
 android:process="com.garena.msdk.pushservice2" >
 <intent-filter>
 <action android:name="com.garena.android.gpush.GNotificationService" />
 </intent-filter>
 </service>
 <receiver
 android:name="com.garena.android.DefaultNotificationReceiver"
 android:enabled="true"
 android:exported="true" >
 <intent-filter>
 <action android:name="com.garena.android.gpns.NOTIFICATION_RECEIVE" />
 <category android:name="com.garena.garena_msdk_sample.app" />
 </intent-filter>
 </receiver>
 <service
 android:name="com.garena.android.gpns.strategy.ServiceLoaderIntentService"
 android:exported="false" />
 <receiver
 android:name="com.garena.android.gpns.logic.UninstallReceiver"
 android:enabled="true"
 android:exported="true" >
 <intent-filter>
 <category android:name="android.intent.category.DEFAULT" />
 <action android:name="android.intent.action.PACKAGE_REMOVED" />
 <data android:scheme="package" />
 </intent-filter>
 </receiver>
 <receiver android:name="com.garena.android.gpns.logic.RebootReceiver">
 <intent-filter>
 <action android:name="android.intent.action.BOOT_COMPLETED"/>
 </intent-filter>
 <intent-filter>
 <action android:name="android.intent.action.EXTERNAL_APPLICATIONS_AVAILABLE"/>
 </intent-filter>
 </receiver>
 <receiver
 android:name="com.garena.android.gpns.strategy.RemoteQueryReceiver"
 android:process="com.garena.msdk.pushservice3">
 <intent-filter>
 <action android:name="com.garena.android.gpns.enquiry"/>
 </intent-filter>
 </receiver>
 </application>
 ```