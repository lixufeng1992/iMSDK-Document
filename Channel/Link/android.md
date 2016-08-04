# Android 配置
```xml
<!-- permission application 节点外-->
<!-- Link 权限-->
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>  


<!-- meta-data 配置  application 节点内-->
<meta-data android:name="com.aiming.link.LinkUrlBase" android:value="@string/link_url_base" />
<meta-data android:name="com.aiming.link.LinkAccessToken" android:value="@string/link_access_token" />
<meta-data android:name="com.aiming.link.TwitterKey" android:value="@string/link_twitter_key" />
<meta-data android:name="com.aiming.link.TwitterSecret" android:value="@string/link_twitter_secret" />
<meta-data android:name="com.facebook.sdk.ApplicationId" android:value="@string/link_facebook_app_id" />
<meta-data android:name="com.facebook.sdk.ApplicationName" android:value="@string/app_name" />
<meta-data android:name="com.google.android.gms.games.APP_ID" android:value="@string/link_google_app_id" />
<meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" /> 

<meta-data android:name="com.aiming.link.DeleteAuthToken" android:value = "@string/link_delete_auth_token"/>
<meta-data android:name="com.aiming.link.debuglevel" android:value = "@string/link_debuglevel"/> <!-- true of false-->

<!-- Activity配置  Application 节点内 -->
<activity
android:name="com.facebook.FacebookActivity"
android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
android:label="@string/app_name"
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    
```