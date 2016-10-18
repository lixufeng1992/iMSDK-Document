### MTA统计配置说明

#### Android 端配置说明
MTA接入和配置参考[http://developer.qq.com/wiki/mta/MTA%E5%9F%BA%E7%A1%80%E4%BB%8B%E7%BB%8D/MTA%E5%9F%BA%E7%A1%80%E4%BB%8B%E7%BB%8D.html](http://developer.qq.com/wiki/mta/MTA%E5%9F%BA%E7%A1%80%E4%BB%8B%E7%BB%8D/MTA%E5%9F%BA%E7%A1%80%E4%BB%8B%E7%BB%8D.html)

```xml
<!-- 权限配置 -->
	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.READ_PHONE_STATE" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

<!-- meta-data 配置 -->
<!-- MTA配置，包括在官网上获取的APPKEY和安装渠道 -->
<meta-data
    android:name="TA_APPKEY"
    android:value="AA4Z1K9BZN39" />



```

