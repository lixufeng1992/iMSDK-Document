### Bugly统计配置说明
#### Android 端配置说明

Bugly 所需的配置，请参考[https://bugly.qq.com/docs/](https://bugly.qq.com/docs/)


```xml
    <!-- 权限配置 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

    <!-- meta-data配置 -->
    <!-- 之前的bugly版本：bugly_1.2.9,  需要在APPID之前添加字符串："bugly" -->
    <meta-data
         android:name="APPID_BUGLY"
         android:value="bugly900003637" />




```
