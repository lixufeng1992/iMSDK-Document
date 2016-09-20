##Help配置    
###1. 配置iMSDK后台

请到iMSDK管理段进行后台配置，联系人RTX：hirryli    
###2.iOS配置    
+ IMSDKAppsetings.bundle中的app.plist设置`IMSDKServerHelp`   

```
<key>IMSDKServerHelp</key>
	<string>http://hk-sdkapi-beta.itop.qq.com</string>
```

###2.Android配置
```  
     
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />


    <activity
        android:name="com.tencent.imsdk.android.help.imsdk.base.IMSDKHelpActivity"
        android:configChanges="locale"
        android:screenOrientation="sensorLandscape"
        android:windowSoftInputMode="stateAlwaysHidden" />
    <activity
        android:name="com.tencent.imsdk.android.help.imsdk.base.IMSDKFeedbackReportActivity"
        android:configChanges="locale"
        android:screenOrientation="sensorLandscape" />
    <activity
        android:name="com.tencent.imsdk.android.help.imsdk.base.IMSDKFeedbackConversationActivity"
        android:configChanges="locale"
        android:screenOrientation="sensorLandscape" />
    <activity
        android:name="com.tencent.imsdk.android.help.imsdk.base.IMSDKFeedbackItemActivity"
        android:configChanges="locale"
        android:screenOrientation="sensorLandscape" />

    <meta-data android:name="IMSDK_SERVER_HELP" android:value="help.itop.qq.com"/>
    <meta-data android:name="IMSDK_SERVER_HELP_SCHEME" android:value="http"/>
``` 
