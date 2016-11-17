# Garena(Android) 工程配置

## Android工程通用配置

注意：Garena Android 的配置可以参考文档：[http://developer.garena.com/docs/msdk/android/getting/started](http://developer.garena.com/docs/msdk/android/getting/started)

1. 权限，分为必选权限和可选项权限

	- 必选权限
	
		```xml
		<uses-permission android:name="android.permission.INTERNET" />
		<uses-permission android:name="com.android.vending.BILLING" />
		<uses-permission android:name="android.permission.READ_LOGS" />
		<uses-permission android:name="android.permission.WAKE_LOCK" />
		<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
		<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
		<uses-permission android:name="android.permission.READ_PHONE_STATE" />
		```

  - 可选权限

		无可选权限

2. 配置

	- ID 配置，该配置项由 Garena 提供，并且测试环境和正式环境不一样
	
		```xml
		<meta-data android:name="com.garena.sdk.applicationId" android:value="1000??" />
		<meta-data android:name="com.tencent.imsdk.garena.APP_SDK_KEY"
			android:value="49c1b7af60b1f5xxxxxxxx" />
		<meta-data android:name="com.garena.sdk.ApplicationSourceId" android:value="2" />
	    ```

    	> 其中:<br>
    	> applicationId 为纯数字;<br>
    	> APP SDK KEY为字符串;<br>
    	> ApplicationSourceId 为渠道 ID，需要根据发布渠道进行区分：2 为 Google 发布渠道，2000 为 Garena 发布渠道 

	- 环境配置，分为测试环境("test",测试环境时将自动开启Garena日志)和正式环境("production"，正式环境时将自动关闭Garena日志)
		
		```xml
		<meta-data android:name="com.tencent.imsdk.garena.Environment" android:value="test" >
		```

	- 推送 ID 配置
	
		```xml
		<meta-data android:name="com.garena.sdk.push.applicationId" android:value="1000??" />
		```

    	> 一般与应用ID（applicationId）一致



	- BeeTalk 登录 Activity 配置

		```xml
		<activity
			android:name="com.beetalk.sdk.BTLoginActivity"
			android:screenOrientation="portrait"
			android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />
		<activity
  			android:name="com.beetalk.sdk.BTBeeTalkAuthActivity"
  			android:screenOrientation="portrait" />
  		<activity
  			android:name="com.beetalk.sdk.plugin.GGPluginActivity"
  			android:configChanges="orientation|screenSize"
  			android:screenOrientation="portrait"
  			android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" />
		```
	- BeeTalk 支付 Activity 配置（请注意：iMSDK并未集成Garena支付功能，添加此配置项是为保证GarenaSDK正常运行）
		
		```xml
		<activity android:name="com.garena.pay.android.GGPayActivity"
  			android:configChanges="orientation"
  			android:exported="true"
  			android:launchMode="singleTop"
  			android:screenOrientation="portrait"
  			android:theme="@style/Theme.Transparent" />
		```
	
	- BeeTalk 统计上报地址，该配置项由 Garena 提供（请注意：iMSDK并未集成Garena上报功能，添加此配置项是为保证GarenaSDK正常运行）

		```xml
		<meta-data android:name="com.beetalklib.ganalytics.report_url" android:value="http://xxx.xxx.xxx.xxx:xxxx" />
		```
	
	- Garena 登录 Activity 配置

		```xml
		<activity
  			android:name="com.beetalk.sdk.GarenaAuthActivity"
  			android:screenOrientation="portrait" />
		```
		
	- Garena 内置了 Facebook 登陆，需要添加如下 Facebook 配置
		
		* App ID 配置
	
			```xml
			<meta-data
	            android:name="com.facebook.sdk.ApplicationId"
	            android:value="\ 427??????????" />
			```
			> 注意：这里的 Facebook App ID 需要以 string 字符串的格式填充，直接填写需在前面添加“\\"和空格
			
		* Facebook Activity 配置
			
			```xml
			<activity android:name="com.facebook.FacebookActivity"
            	android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
            	android:theme="@android:style/Theme.Translucent.NoTitleBar"
            	android:label="@string/app_name" />
			```
		
		* 如果需要使用 Facebook 的图片、视频等多媒体分享功能，还需要添加如下配置
		
			```xml
			<provider
				android:authorities="com.facebook.app.FacebookContentProvider[Facebook App ID]"
           	android:name="com.facebook.FacebookContentProvider"
           	android:exported="true" />
			```
			
			> 其中，[Facebook App ID] 需要替换成应用的 Facebook ID
		
	- Garena 推送配置（请注意：iMSDK并未集成Garena推送功能，添加此配置项是为保证GarenaSDK正常运行）
	
		* Receiver 配置

			```xml
			<receiver android:name="com.garena.android.gpns.logic.AlarmReceiver"
	  			android:process="com.garena.msdk.pushservice2" >
				<intent-filter>
	  				<action android:name="com.garena.android.gpns.ALARM_ACTION1000??" />
				</intent-filter>
			</receiver>
			<receiver
				android:name="com.garena.android.DefaultNotificationReceiver"
				android:enabled="true"
			  	android:exported="true" >
				<intent-filter>
				  	<action android:name="com.garena.android.gpns.NOTIFICATION_RECEIVE" />
					<category android:name="com.garena.garena_msdk_sample.app" />
				</intent-filter>
			</receiver>
			```
			> 其中，intent-filter 的值最后续加上 Application ID，如：
			```xml
			<action android:name="com.garena.android.gpns.ALARM_ACTION100010" />
			```
			> com.garena.garena_msdk_sample.app 需要修改成游戏包名
			
		* Service 配置
		
			```xml
			<service android:name="com.garena.android.gpns.GNotificationService"
			  	android:enabled="true"
			  	android:exported="true"
			  	android:process="com.garena.msdk.pushservice2" >
				<intent-filter>
			  		<action android:name="com.garena.android.gpush.GNotificationService" />
				</intent-filter>
			</service>
			```
			
		* 其他配置
			
			```xml
			<service
  				android:name="com.garena.android.gpns.strategy.ServiceLoaderIntentService"
  				android:exported="false" />
			```


		* 卸载相关配置
			
			```xml
			<receiver
			 	android:name="com.garena.android.gpns.logic.UninstallReceiver"
			  	android:enabled="true"
			  	android:exported="true" >
				<intent-filter>
					<category android:name="android.intent.category.DEFAULT" />
			  		<action android:name="android.intent.action.PACKAGE_REMOVED" />
			  		<data android:scheme="package" />
				</intent-filter>
			</receiver>
			```
	
		* 重启相关
		
			```xml
			<receiver android:name="com.garena.android.gpns.logic.RebootReceiver">
				<intent-filter>
			  		<action android:name="android.intent.action.BOOT_COMPLETED"/>
				</intent-filter>
				<intent-filter>
			  		<action android:name="android.intent.action.EXTERNAL_APPLICATIONS_AVAILABLE"/>
				</intent-filter>
			</receiver>
			```
	
		* 其他
			
			```xml
			<receiver
			  	android:name="com.garena.android.gpns.strategy.RemoteQueryReceiver"
			  	android:process="com.garena.msdk.pushservice3">
				<intent-filter>
			  		<action android:name="com.garena.android.gpns.enquiry"/>
				</intent-filter>
			</receiver>
			```


