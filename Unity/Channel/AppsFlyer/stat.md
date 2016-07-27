# AppsFlyer 统计功能说明

## AppsFlyer 统计功能说明

### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | :--: |:-------: | :-----: | :--: |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | √ | - |
| 3 | public void reportEvent | 事件上报 | √ | - |
| 4 | public void reportPurchase() | 购买行为上报 | √ | - |
| 5 | public void trackEvent() | 事件跟踪 | x | - |
| 6 | public bool trackPage() | 页面跟踪 | x | - |
| 7 | public void speedTest() | 测速 | x | - |
| 8 | public void reportCrash() | 获取当前登录返回数据 | x | - | 
| 9 | public void reportAutoExceptionReport() | 登出当前渠道 | x | - |


### AppsFlyer统计配置说明

 #### Android 端配置说明
 ``` xml
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