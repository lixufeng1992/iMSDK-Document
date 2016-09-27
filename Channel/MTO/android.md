## MTO Android 工程配置  

```
<?xml version="1.0" encoding="utf-8"?>
<manifest
    xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.tencent.imsdk"
    android:versionCode="1"
    android:versionName="1" >
    <uses-sdk
        android:minSdkVersion="15"
        android:targetSdkVersion="23" />
    <permission
        android:name="YOUR_PACKAGE.C2D_MESSAGE"
        android:protectionLevel="signature" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
    <uses-permission android:name="YOUR_PACKAGE.permission.C2D_MESSAGE" />
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />    
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="com.android.vending.BILLING" />

    <uses-feature
        android:name="android.hardware.camera"
        required="false" />
    <uses-feature
        android:name="android.hardware.camera.autofocus"
        required="false" />

    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.USE_CREDENTIALS" />
    <uses-permission android:name="com.zing.zalo.permission.ACCESS_THIRD_PARTY_APP_AUTHORIZATION" />
    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:name="com.android.m6.guestlogin.MTOApplication"
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
		
		<!-- vng gameid define, can not empty & must right value -->
        <meta-data
            android:name="appID"
            android:value="your_appID" />
        <meta-data
            android:name="mto_game_id"
            android:value="your_gameId" />
        <meta-data
            android:name="mto_payment_key_1"
            android:value="your_appKey" />        

        <meta-data
            android:name="configOffSuccessDialog"
            android:value="true" />
        <meta-data
            android:name="configFullScreen"
            android:value="true" />
        <meta-data
            android:name="configLoginChannel"
            android:value="0" />
        <meta-data
            android:name="conversion_id"
            android:value="your_conversion id" />
        <meta-data
            android:name="mto_label"
            android:value="mto_label" />
        <meta-data
            android:name="sender_id"
            android:value="your_sender_id" />
        <meta-data
            android:name="mto_AgeValidation"
            android:value="your_mto_AgeValidation" />
        <meta-data
            android:name="googleWalletPubKey"
            android:value="your_googleWalletPubKey" />
        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
        <meta-data
            android:name="com.facebook.sdk.ApplicationId"
            android:value="your facebook applicationId" />
        
        <activity
            android:name="com.android.m6.guestlogin.ui.ZaloAutoLoginActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.tencent.imsdk.unity.mto.UnityPlayerNativeActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:icon="@drawable/ic_launcher"
            android:label="@string/app_name"
            android:screenOrientation="landscape"
            android:singleUser="true"
            android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name="com.zing.zalo.zalosdk.payment.direct.PaymentGatewayActivity"
            android:configChanges="orientation|keyboardHidden|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        
        
        <!-- New Payment -->
        <activity
            android:name="vn.zing.pay.zmpsdk.view.PaymentGatewayActivity"
            android:launchMode="singleTask"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data
                    android:host="payment-cancel"
                    android:scheme="paymentsdk-15" />
                <data
                    android:host="payment-complete"
                    android:scheme="paymentsdk-15" />
            </intent-filter>
        </activity>
        <activity
            android:name="vn.zing.pay.zmpsdk.view.PaymentChannelActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar"
            android:windowSoftInputMode="stateHidden|stateAlwaysHidden" >
        </activity>
        <!-- End of new payment -->

        <activity
            android:name="vn.com.vng.so6wallet.m.M_PaymentActivity"
            android:configChanges="orientation|keyboardHidden|screenSize"
            android:launchMode="singleTask"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.zing.zalo.zalosdk.payment.direct.CameraActivity"
            android:configChanges="keyboardHidden|screenSize|orientation"
            android:launchMode="singleTop"
            android:theme="@android:style/Theme.Black.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.zing.zalo.zalosdk.payment.direct.ReviewActivity"
            android:configChanges="keyboardHidden|screenSize|orientation"
            android:launchMode="singleTop"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.android.m6.guestlogin.ui.LoginActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.android.m6.guestlogin.ui.SeaAutoLoginActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.android.m6.guestlogin.ui.PaymentChosen"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.facebook.FacebookActivity"    
            android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
            android:label="@string/app_name"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" />

        <receiver
            android:name="com.google.android.gms.gcm.GcmReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="com.vng.sea.sdk.push.GcmBroadcastReceiver"
            android:permission="com.google.android.c2dm.permission.SEND" >
            <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />

                <category android:name="com.vng.wemoba" />
            </intent-filter>
        </receiver>

        <service android:name="com.vng.sea.sdk.push.GCMNotificationIntentService" />

        <receiver
            android:name="com.google.android.gms.gcm.GcmReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
            </intent-filter>
        </receiver>

        <!-- The AppsFlyer Install Receiver is first and will broadcast to all receivers placed below it -->
        <receiver
            android:name="com.appsflyer.MultipleInstallBroadcastReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.android.vending.INSTALL_REFERRER" />
            </intent-filter>
        </receiver>
        <!-- —All other receivers should follow right after --> 
        <receiver
            android:name="com.google.android.apps.analytics.AnalyticsReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.android.vending.INSTALL_REFERRER" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="com.admob.android.ads.analytics.InstallReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.android.vending.INSTALL_REFERRER" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="com.google.ads.conversiontracking.InstallReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.android.vending.INSTALL_REFERRER" />
            </intent-filter>
        </receiver>

		
		
		
        <!-- AppsFlyer -->
        <meta-data
            android:name="APPSFLYER_KEY"
            android:value="your_APPSFLYER_KEY" />			

		
		<meta-data android:name="com.tencent.imsdk.mto.GameVersion" android:value="your gameVersion" />	


    <!-- Add for VNG-SEA-SDK-Release(0923) -->
    <activity         
        android:name="com.android.m6.guestlogin.M6_CustomFBActivity"                        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"         
android:screenOrientation="landscape"         
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >     
</activity>      
<provider          
android:authorities="com.facebook.app.FacebookContentProvider1035456593228820"         android:name="com.facebook.FacebookContentProvider"         
android:exported="true"/>     
<activity         
android:name="vn.com.vng.fbsocial.FBActivityHandling"         android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"        
 android:screenOrientation="landscape"         
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >    
 </activity>

<activity         
android:name="vn.zing.pay.zmpsdk.view.PaymentGatewayActivity"         
android:launchMode="singleTask"         
android:theme="@android:style/Theme.DeviceDefault.Light" >         
<intent-filter>             
<action android:name="android.intent.action.VIEW" />             
<category android:name="android.intent.category.DEFAULT" />             
<category android:name="android.intent.category.BROWSABLE" />             
<data                
 android:host="payment-cancel"                 
android:scheme="paymentsdk-15" />             
<data                 
android:host="payment-complete"                
 android:scheme="paymentsdk-15" />          
</intent-filter>     
</activity>     
<activity         
android:name="vn.zing.pay.zmpsdk.view.PaymentChannelActivity"         
android:theme="@android:style/Theme.DeviceDefault.Light"         
android:windowSoftInputMode="stateHidden|stateAlwaysHidden" >     
</activity>     
<service        
android:name="vn.zing.pay.zmpsdk.business.inappbilling.TGoogleIABRetryVerifyReceiptService"         
android:exported="false" />





		

    </application>

</manifest>


```