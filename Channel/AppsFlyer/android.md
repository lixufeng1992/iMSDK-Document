## 6.18.2 AppsFlyer工程配置

### 配置说明

* 权限配置，在AndroidManifest.xml中增加如下权限

    ```xml
	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />	
	<uses-permission android:name="android.permission.WAKE_LOCK" />
	<permission android:name=".permission.C2D_MESSAGE" android:protectionLevel="signature" />
	<uses-permission android:name=".permission.C2D_MESSAGE" />
	<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    ```	
 
* AppsFlyer 信息配置

    ```xml
	<meta-data android:name="DEVKEY_APPSFLYER" android:value="your_devkey" />
    ```
 
* Receiver 配置，在 Application 节点下，添加相应的配置。注意：需要尽量将 Appsflyer 的 Receiver 放到前面，以提高 Appsflyer 数据的准确性
 
   ``` xml 

   <receiver android:name="com.appsflyer.MultipleInstallBroadcastReceiver" android:exported="true">
       <intent-filter>
           <action android:name="com.android.vending.INSTALL_REFERRER"/>
       </intent-filter>
   </receiver>
   <receiver android:name="com.google.android.gms.gcm.GcmReceiver" android:exported="true">
       <intent-filter>
           <action android:name="com.google.android.c2dm.intent.RECEIVE"/>
       </intent-filter>
   </receiver>	
	
 	```
* Google GCM 服务版本配置
 
    ```xml
    <meta-data android:name="com.google.android.gms.version"
    android:value="@integer/google_play_services_version" />
    ```
    > google_play_services_version 一般可以在 Google GMS 工程中的 xml 中可以找到

* Appsflyer 4.5 以上版本（对应 IMSDK 1.8 版本及以上），需要添加 Google GMS 配置以支持 卸载跟踪
     
     * Google GCM 推送 ID 信息配置
 
 	```xml
 	<meta-data android:name="GCM_PROJECT_NUM" android:value="your_gcm_project_num"/>
 	```
 
## 版本更新说明
 
* 1.8.0版本后，增加卸载追踪功能，并更新依赖的AppsFlyer版本
* 1.9.0版本， 需在游戏主activity，onCreate()中调用ExtendAppsFlyer.onCreate(Context context)
* 2.0.0版本后，需在onCreate()中调用
    ```code
    IMSDKStat.initialize(this);    
    if(IMSDKStat.initChannel("AppsFlyer", new String[]    {IStat.STAT_EVENT_INITIALIZE})){ IMLogger.d("init AppsFlyer OK");};
    ```
* your_devkey 需替换成游戏自己的AppsFlyer Key，该值需到[AppsFlyer官网](https://www.appsflyer.com/)申请
* your_gcm_project_num需替换成游戏自己的Google GCM Project NUM，该值申请参考[GoogleGCMProjectNUM 获取](https://support.appsflyer.com/hc/en-us/articles/208004986)

 
 