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