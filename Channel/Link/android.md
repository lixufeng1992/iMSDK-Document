## 6.9.2 Android 配置

* 权限配置
```xml
<!-- permission application 节点外-->
<!-- Link 权限-->
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>  
```

```xml
<!-- meta-data 配置  application 节点内-->
<!-- 请配置如下meta-data 配置 -->

<meta-data android:name="com.aiming.link.LinkUrlBase" android:value="{your linkUrlBase}" />
<meta-data android:name="com.aiming.link.LinkAccessToken" android:value="{your linkAccessToken}" />
<meta-data android:name="com.aiming.link.TwitterKey" android:value="{your linkTwitterKey}" />
<meta-data android:name="com.aiming.link.TwitterSecret" android:value="@string/link_twitter_secret" />
<meta-data android:name="com.facebook.sdk.ApplicationId" android:value="\ {your facebookApplicationId}" />
<meta-data android:name="com.facebook.sdk.ApplicationName" android:value="{your facebookApplicationName}" />
<meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ {your gms appID}" />
<meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" /> 

<!-- com.aiming.link.DeleteAuthToken请通过 string.xml文件配置进行读取 -->
<meta-data android:name="com.aiming.link.DeleteAuthToken" android:value = "@string/link_delete_auth_token"/> <!-- true of false-->
<meta-data android:name="com.aiming.link.debuglevel" android:value = "@string/link_debuglevel"/> <!-- true of false-->

<!-- Activity配置  Application 节点内 -->
<activity
android:name="com.facebook.FacebookActivity"
android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
android:label="@string/app_name"
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    
```