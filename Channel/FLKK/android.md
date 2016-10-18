###　Android 工程配置

* 权限配置
    
    请在工程中AndroidManifest中添加如下权限
``` xml
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.WAKE_LOCK" />
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.GET_TASKS" />
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```
* 入口Application配置
    
    FLKK渠道需要抢占入口Application， 请在工程主AndroidManifest中，找到Application节点，并将name属性值改为如下：

```
  <application
      android:name="com.tencent.imsdk.unity.flkk.IMSDKFLKKApplication"
      android:theme="@android:style/Theme.NoTitleBar" android:icon="@drawable/app_icon"                 
      android:label="@string/app_name" 
      android:debuggable="true">
```

* Activity配置

    请在主工程AndroidManifest.xml文件中Application节点里添加如下Activity配置

```xml
<activity 
    android:name="com.tencent.imsdk.unity.flkk.UnityPlayerNativeActivity" 
    android:label="@string/app_name">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
        <category android:name="android.intent.category.LEANBACK_LAUNCHER" />
    </intent-filter>
</activity>



 <activity android:name="com.feiliu.gameplatform.popwindow.FLSdkActivity" > </activity>

 <activity android:name="com.feiliu.gameplatform.popwindow.FLUserAgreementActivity" > </activity>

 <activity

 android:name="com.feiliu.gameplatform.FLGooglePlayActivity"

 android:background="#e0000000"

 android:theme="@android:style/Theme.Translucent" >

 </activity>

 <meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
```

