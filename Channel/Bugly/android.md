### Bugly统计配置说明
#### Android 端配置说明

Bugly 所需的配置，请参考[https://bugly.qq.com/docs/](https://bugly.qq.com/docs/)

```xml
    <!-- 1.x.x配置 -->
    <!-- 权限配置 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

    <!-- meta-data配置 -->
    <meta-data
         android:name="APPID_BUGLY"
         android:value="\ 900003637" />


```

注：2.x.x版本配置有变
``` xml
    <!-- 2.x.x 配置 -->
    <!-- 权限配置 -->
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />        
    <uses-permission android:name="android.permission.INTERNET" />    
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />    
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />    
    <uses-permission android:name="android.permission.READ_LOGS" />

    <!-- meta-data配置 -->
    <!-- BUGLY_APPID 值改成游戏自己的ID -->
        <meta-data
            android:name="BUGLY_APPID"
            android:value="900003637" />


    <!-- 可选配置 -->
         <!-- BUGLY_ENABLE_DEBUG ,建议测试设成true， 发布设成false -->
         <meta-data
            android:name="BUGLY_ENABLE_DEBUG"
            android:value="true" />
        <!-- 配置APP版本号 -->
        <meta-data
            android:name="BUGLY_APP_VERSION"
            android:value="1.0.1" />
        <!-- 配置APP渠道号 -->
        <meta-data
            android:name="BUGLY_APP_CHANNEL"
            android:value="IMSDK" />
        <!-- 配置Bugly调试模式（true或者false）-->
        

    



```
