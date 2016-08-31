## 6.10.1 Stove(Android) 工程配置

### Android工程通用配置

* Stove在AndroidManifest.xml中配置如下
 ```xml
 <!-- Stove_1.11.0 start -->
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> <!-- Check the network status -->
 <uses-permission android:name="android.permission.GET_TASKS" /> <!-- Retrieve task info -->
 <uses-permission android:name="android.permission.INTERNET" /> <!-- Use the internet -->
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /> <!-- Check the wifi status -->
 <uses-permission android:name="android.permission.READ_PHONE_STATE" /> <!-- Read the device ID and USIM information -->
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> <!-- Write the external memory -->
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" /> <!-- Read the external memory -->
 <uses-feature
     android:name="android.hardware.telephony"
     android:required="false" />
 <!-- GCM -->
 <permission
     android:name="{your_package_name}.permission.C2D_MESSAGE"
     android:protectionLevel="signature" /> <!-- Use GCM -->
 <uses-permission android:name="{your_package_name}.permission.C2D_MESSAGE" /> <!-- Avoid the GCM message crash with other applications -->
 <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" /> <!-- Receive the GCM messages -->
 <uses-permission android:name="android.permission.GET_ACCOUNTS" /> <!-- Retrieve accounts -->
 <uses-permission android:name="android.permission.WAKE_LOCK" /> <!-- Alarm -->
 <uses-permission android:name="com.android.vending.BILLING" /> <!-- Use In-App Billing -->
 <uses-permission android:name="android.permission.RECORD_AUDIO" /> <!-- Use recording: Remove when Lite Ver is applied -->
 <uses-permission android:name="android.permission.READ_CONTACTS" /> <!-- Retrieve contacts: Remove if Google featured -->
 <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" /> <!-- Notification window: Remove if Google featured -->
 <!-- Stove_1.11.0 end -->

 <application
     android:allowBackup="true"
     android:icon="@drawable/ic_launcher"
     android:label="@string/app_name">
 <!-- Stove_1.11.0 start -->
 <activity
     android:name="com.stove.stovesdk.activity.StoveActivity"
     android:configChanges="keyboardHidden|orientation|screenLayout|screenSize"
     android:theme="@style/Theme.StoveTransparent" >
 </activity>
 <activity
     android:name="com.facebook.FacebookActivity"
     android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
     android:label="@string/app_name"
     android:theme="@style/Theme.StoveTransparent" />
 <!-- GCM Receiver -->
 <receiver
     android:name="com.stove.stovesdkcore.gcm.MyBroadcastReceiver"
     android:permission="com.google.android.c2dm.permission.SEND" >
 <intent-filter>
     <action android:name="com.google.android.c2dm.intent.RECEIVE" />
     <action android:name="com.google.android.c2dm.intent.REGISTRATION" />
 <category android:name="{your_package_name}" />
 </intent-filter>
 </receiver>
 <!-- STOVE SDK Receiver -->
 <receiver android:name="com.stove.stovesdkcore.receiver.ReferrerReceiver" >
 <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
 </intent-filter>
 </receiver>
 <!-- GCM IntentService -->
     <service android:name="com.stove.stovesdkcore.gcm.MyIntentService" />
     <service android:name="com.stove.stovesdkcore.service.HeartbeatService" />
 <!-- Remove if the Messenger Service Lite Ver is applied -->
 <!-- <service android:name="com.stove.messenger.service.MessengerService" /> -->
 <service
     android:name="com.stove.messenger.service.MessengerWidgetService"
     android:exported="true" >
 <intent-filter>
     <action android:name="com.stove.messenger.MessengerWidgetService" />
 </intent-filter>
 </service>
 <!-- Messenger Provider. Remove if Lite Ver is applicable -->
 <!-- <provider
     android:name="com.stove.messenger.database.MessengerProvider"
     android:authorities="{your_package_name}"
     android:exported="true" /> -->
 <provider
     android:name="com.facebook.FacebookContentProvider"
     android:authorities="{your_package_name}"
     android:exported="true" />
 <!-- Facebook app ID -->
 <meta-data
     android:name="com.facebook.sdk.ApplicationId"
     android:value="\ {your_facebook_app_id}" />
 <!-- Google Library Version -->
 <meta-data
     android:name="com.google.android.gms.version"
     android:value="{your_google_gms_version}" />
 <!-- Stove_1.11.0 end -->
 </application>
 ```