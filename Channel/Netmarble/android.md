## Netmarble 工程配置

### Android工程配置

* 1. 权限配置

请在AndroidManifest.xml文件中增加如下权限配置
```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET" />

<!-- 下面三个个权限需要添加，否则初始化不成功 -->
<uses-permission android:name="android.permission.VIBRATE" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.GET_TASKS" />
```
* 2. Meta-data配置

配置Kakao AppKey
```
<meta-data    
    android:name="com.kakao.sdk.AppKey"    
    android:value="@string/kakao_app_key" />
```

配置ChannelSigninTimeout值（可选，不填此配置项，则默认10000毫秒，表示Netmarble自动登录kakao回调超时时间）
```
<meta-data 
    android:name="com.tencent.imsdk.netmarble.ChannelSigninTimeout"    
    android:value="10000" />
```

* 3. Activity和Provider配置

```
<activity
    android:name="com.netmarble.LoginActivity"
    android:configChanges="orientation|keyboardHidden|screenSize" />

<provider    
    android:name="com.netmarble.contentprovider.NetmarbleContentProvider"    
    android:authorities="{your_packageName}"     
    android:exported="true" >
```
> 将your_packageName改成应用包名
