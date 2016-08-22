##Android工程配置     
###1 在Assets/Plugins/Android 目录下找到AndroidManifest.xml文件，添加
```
// 权限（Application 节点外）	
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	
	<application>
		<receiver 
			android:name="com.google.ads.conversiontracking.InstallReceiver"
			android:exported="true">
			<intent-filter>
				<action android:name="com.android.vending.INSTALL_REFERRER" />
			</intent-filter>
		</receiver>

		<meta-data android:name="GoogleAdwords_ConversionId" android:value="\ {your_conversionId}" />
		
	</application>
```
