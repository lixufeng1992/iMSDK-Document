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
<meta-data    android:name="com.kakao.sdk.AppKey"    android:value="{your_kakao_appkey}" />
```

配置ChannelSigninTimeout值（可选，默认10000毫秒，表示Netmarble自动登录kakao回调超时时间）
```
<meta-data 
    android:name="com.tencent.imsdk.netmarble.ChannelSigninTimeout"    android:value="10000" />

```


* 3. Activity和Provider配置
