### Beacon统计功能配置说明

####　Android端配置说明

Beacon接入和配置参考

```xml
<!-- 权限配置 -->
	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.READ_PHONE_STATE" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />


<!-- meta-data 配置 -->
<!-- 官网上获取的APPKEY， 如0I40061SZ81FIQ8L -->
<meta-data
    android:name="APPKEY_DENGTA"
    android:value="{your appkey}" />




```