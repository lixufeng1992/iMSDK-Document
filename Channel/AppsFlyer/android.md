### 6.18.2 AppsFlyer工程配置

* 权限配置
 
 
 * iMSDK appsflyer 统计插件版本1.6.0 和 1.6.1版本请用如下配置
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

* iMSDK appsflyer 统计插件版本1.8.0 及以上版本请用如下配置
> 1.8.0及以上版本以来新的appsflyer三方包（4.5.0），增加卸载追踪功能


 ``` xml 
 <!-- version 1.8.0 and upper add uninstall function -->
 <!-- version 1.8.0 and upper -->
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
* 1.8.0版本后，增加卸载追踪功能，并更新依赖的AppsFlyer版本
* 1.9.0版本， 需在游戏主activity，onCreate()中调用ExtendAppsFlyer.onCreate(Context context)
* 2.0.0版本后，需在onCreate()中调用
```code
    IMSDKStat.initialize(this);    
    if(IMSDKStat.initChannel("AppsFlyer", new String[]    {IStat.STAT_EVENT_INITIALIZE})){ IMLogger.d("init AppsFlyer OK");};
```
* your_devkey 需替换成游戏自己的AppsFlyer Key，该值需到[AppsFlyer官网](https://www.appsflyer.com/)申请
* your_gcm_project_num需替换成游戏自己的Google GCM Project NUM，该值申请参考[GoogleGCMProjectNUM 获取](https://support.appsflyer.com/hc/en-us/articles/208004986)

 
 