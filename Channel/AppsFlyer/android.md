### AppsFlyer统计配置说明

 #### Android 端配置说明
 ``` xml 
 <!-- version 1.6.0 and 1.6.1 -->
    <uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />	
	<uses-permission android:name="android.permission.WAKE_LOCK" />
    <permission android:name=".permission.C2D_MESSAGE"
        android:protectionLevel="signature" />
    <uses-permission android:name=".permission.C2D_MESSAGE" />
	<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />	
	<application>
		<!-- AppsFlyer 安装receiver -->
	<receiver android:name="com.appsflyer.MultipleInstallBroadcastReceiver" android:exported="true">
	<intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
	</receiver>	
	<receiver
		android:name="com.google.android.gms.gcm.GcmReceiver"
		android:exported="true">
		<intent-filter>
			<action android:name="com.google.android.c2dm.intent.RECEIVE" />
		</intent-filter>
	</receiver>
	<!-- Appsflyer配置，需要配置在官网上获取的DEVKEY --> 
	<meta-data
            android:name="DEVKEY_APPSFLYER"
            android:value="your_devkey" />
	<!--AppsFlyer can track Google Advertising ID to improve tracking, 假如项目需要，需要添加以下配置，详细参考Android AppsFlyer说明文档3.4节 -->
	<meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
    <!-- GCM Project NUM -->			
	<meta-data android:name="GCM_PROJECT_NUM" android:value="your_gcm_project_num"/>
 ```

 -----------------
 ``` xml 
 
 
 <?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
	package="com.tencent.imsdk.appsflyer.stat">
	
	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	
	<uses-permission android:name="android.permission.WAKE_LOCK" />

    <permission android:name=".permission.C2D_MESSAGE"
        android:protectionLevel="signature" />
    <uses-permission android:name=".permission.C2D_MESSAGE" />
	<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
	
	<application>
		<!-- AppsFlyer 安装receiver -->
	<receiver android:name="com.appsflyer.MultipleInstallBroadcastReceiver" android:exported="true">
	<intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
	</receiver>
	
	<receiver
		android:name="com.google.android.gms.gcm.GcmReceiver"
		android:exported="true">
		<intent-filter>
			<action android:name="com.google.android.c2dm.intent.RECEIVE" />
		</intent-filter>
	</receiver>
	<!-- Appsflyer配置，需要配置在官网上获取的DEVKEY --> 
	<meta-data
            android:name="DEVKEY_APPSFLYER"
            android:value="your_devkey" />
	<!--AppsFlyer can track Google Advertising ID to improve tracking, 假如项目需要，需要添加以下配置，详细参考Android AppsFlyer说明文档3.4节 -->
	<meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
			
	<meta-data android:name="GCM_PROJECT_NUM" android:value="your_gcm_project_num"/>
	
	</application>

</manifest>

```
 
 