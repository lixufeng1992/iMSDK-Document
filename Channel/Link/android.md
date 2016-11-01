## 6.9.2 Android 配置

* 权限配置

    请在主工程AndroidManifest.xml文件中添加如下权限配置
```xml
<!-- permission application 节点外-->
<!-- Link 权限-->
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>  
```

* Activity节点配置

    请在主工程AndroidManifest.xml文件中Application节点里添加如下Activity配置
```xml
<activity
    android:name="com.facebook.FacebookActivity"
    android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
    android:label="@string/app_name"
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
```
* meta-data配置
    
    请在主工程AndroidManifest.xml文件中Application节点里添加如下Activity配置 
     
```xml
    <meta-data android:name="com.aiming.link.LinkUrlBase" android:value="{your linkUrlBase}" />
    <meta-data android:name="com.aiming.link.LinkAccessToken" android:value="{your linkAccessToken}" />
    <meta-data android:name="com.aiming.link.TwitterKey" android:value="{your linkTwitterKey}" />
    <meta-data android:name="com.aiming.link.TwitterSecret" android:value="@string/link_twitter_secret" />
    <meta-data android:name="com.facebook.sdk.ApplicationId" android:value="\ {your facebookApplicationId}" />
    <meta-data android:name="com.facebook.sdk.ApplicationName" android:value="{your facebookApplicationName}" />
    <meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ {your gms appID}" />
    <!-- 以上配置具体的值请联系Link方进行获取 -->
    <meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />     
    <!-- com.aiming.link.DeleteAuthToken请通过 string.xml文件配置进行读取 -->
    <meta-data android:name="com.aiming.link.DeleteAuthToken" android:value = "@string/link_delete_auth_token"/>     <!-- true of false-->
    <meta-data android:name="com.aiming.link.debuglevel" android:value = "@string/link_debuglevel"/> <!-- true of false-->
```
> com.aiming.link.DeleteAuthToken 标记用户删除App再重新安装，是否可以删除以前的LinkAuthToken， 具体为下：设置为 true， 在App第一次启动时，会自动删除以前老的LinkAuthToken，获取新的LinkAuthToken，设置为false或者不设置，则会继承之前的LinkAuthToken。 


