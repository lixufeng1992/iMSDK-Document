
## VNG Android 工程配置(VNGSEA配置与VNG类似，请参考下方“VNGSEA Android”)

请在工程主AndroidManifest.xml文件中加入如下配置

```xml
  <uses-permission android:name="android.permission.INTERNET"/>
  <permission android:name="{your_packagename}.C2D_MESSAGE" android:protectionLevel="signature"/>
  <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>
  <uses-permission android:name="{your_packagename}.permission.C2D_MESSAGE"/>
  <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE"/>
  <uses-permission android:name="android.permission.GET_ACCOUNTS"/>
  <uses-permission android:name="android.permission.WAKE_LOCK"/>
  <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  <uses-permission android:name="android.permission.CAMERA"/>
  <uses-permission android:name="com.android.vending.BILLING"/>
  <uses-permission android:name="android.permission.USE_CREDENTIALS"/>
  <uses-permission android:name="com.zing.zalo.permission.ACCESS_THIRD_PARTY_APP_AUTHORIZATION"/>

  <application
        android:name="com.android.m6.guestlogin.MTOApplication"
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
		
		<!-- MAIN_ACTIVITY pls copy "intent-filter node" for schemeUrl if replace MAIN_ACTIVITY-->
		<activity
            android:name="com.tencent.imsdk.unity.vng.UnityPlayerNativeActivity"
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
			<!-- "intent-filter node" for schemeUrl start-->
			<intent-filter>
                <data android:scheme="{your_packagename}" />
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
            </intent-filter>
			<!-- "intent-filter node" for schemeUrl end-->
        </activity>
		
		<meta-data android:name="mto_game_id" android:value="{your_vng_game_id}"/>
		<meta-data android:name="com.tencent.imsdk.vng.GameVersion" android:value="{your_vng_version}"/>
		
		<meta-data
            android:name="configOffSuccessDialog"
            android:value="true" />
        <meta-data
            android:name="configFullScreen"
            android:value="true" />
        <meta-data
            android:name="appID"
            android:value="{your_appID}" />
        <meta-data
            android:name="configLoginChannel"
            android:value="0" />
        <!-- Using sender_id for AF Uninstall -->
        <meta-data
            android:name="sender_id"
            android:value="{your_sender_id}" />
        <meta-data
            android:name="conversion_id"
            android:value="{your_conversion_id}" />
        <meta-data
            android:name="mto_label"
            android:value="{your_mto_label}" />

        <!-- Define for interaction with google sdk -->
        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
        <!-- Define for interaction with facebook sdk -->

		
		
        <activity
            android:name="vn.com.vng.corelogin.data.MTO_ForcePAActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:theme="@android:style/Theme.Translucent" >
        </activity>
        <!-- Ending of Login M6_Zalo_Login configuration -->


        <!-- Get Friend list facebook  configuration -->
        <activity
            android:name="com.android.m6.guestlogin.M6_CustomFBActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <!-- Ending of getting friend list facebook  configuration -->
        <meta-data
            android:name="com.facebook.sdk.ApplicationId"
            android:value="@string/facebook_app_id" />

        <provider
            android:name="com.facebook.FacebookContentProvider"
            android:authorities="com.facebook.app.FacebookContentProvider{your_facebook_app_id}"
            android:exported="true" />

        <activity
            android:name="vn.com.vng.fbsocial.FBActivityHandling"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>

        <!-- Zalo Social -->
        <activity
            android:name="vn.com.vng.social.ZaloSendImageMgsActivity"
            android:configChanges="orientation|keyboardHidden"
            android:label="@string/title_activity_zalo_send_image_mgs"
            android:theme="@style/PopupTheme"
            android:windowSoftInputMode="adjustPan|adjustResize|stateHidden" >
        </activity>
        <activity
            android:name="vn.com.vng.social.UploadPhotoActivity"
            android:configChanges="orientation|keyboardHidden"
            android:label="@string/title_activity_upload_photo"
            android:theme="@style/PopupTheme"
            android:windowSoftInputMode="adjustPan|adjustResize|stateHidden" >
        </activity>
        <activity
            android:name="vn.com.vng.social.ZaloInviteFriendActivity"
            android:configChanges="orientation|keyboardHidden"
            android:label="@string/title_activity_zalo_invite_friend"
            android:theme="@style/PopupTheme"
            android:windowSoftInputMode="adjustPan|adjustResize|stateHidden" >
        </activity>
        <activity
            android:name="vn.com.vng.social.PhotoFolderActivity"
            android:configChanges="orientation|keyboardHidden"
            android:label="@string/title_activity_zalo_invite_friend"
            android:theme="@style/PopupTheme"
            android:windowSoftInputMode="adjustPan|adjustResize|stateHidden" >
        </activity>
        <!-- Ending ofZalo Social -->
        <!-- Login M6_Zalo_Login configuration -->
        <activity
            android:name="com.android.m6.guestlogin.M6_ZaloLoginActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:launchMode="singleTask"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.zing.zalo.zalosdk.oauth.WebLoginActivity"
            android:launchMode="singleTask"
            android:theme="@android:style/Theme.Translucent.NoTitleBar"
            android:windowSoftInputMode="stateHidden|stateAlwaysHidden" >
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data
                    android:host="oauthcode"
                    android:scheme="zalo-1812423796061342251" />
            </intent-filter>
        </activity>
        <!-- Ending of Login M6_Zalo_Login configuration -->
        <activity
            android:name="com.facebook.FacebookActivity"
            android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
            android:label="@string/app_name"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="vn.com.vng.mto.sdk.MTO_MainLoginActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:launchMode="singleTask"
            android:screenOrientation="sensorLandscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="vn.com.vng.corelogin.data.M6_AutoLoginHandle"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>

        <!-- New Payment -->
        <activity
            android:name="vn.zg.py.zmpsdk.view.PtClActivity"
            android:launchMode="singleTask"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data
                    android:host="payment-cancel"
                    android:scheme="paymentsdk-33" />
                <data
                    android:host="payment-complete"
                    android:scheme="paymentsdk-33" />
            </intent-filter>
        </activity> 

        <service
            android:name="vn.zg.py.zmpsdk.business.iab.TGoogleIABRetryVerifyReceiptService"
            android:exported="false" />
        <!-- End of new payment -->

        <activity
            android:name="com.zing.zalo.zalosdk.payment.direct.CameraActivity"
            android:configChanges="keyboardHidden|screenSize|orientation"
            android:launchMode="singleTop"
            android:theme="@android:style/Theme.Black.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.android.m6.guestlogin.RequestRunTimePermissionActivity"
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
            android:name="com.android.m6.guestlogin.ui.PaymentChosen"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="com.facebook.LoginActivity"
            android:label="@string/title_facebook_login" >
        </activity>

        <!-- AppsFlyer: Referrer broadcast receiver. Must be the first receiver within the <application> tag -->
        <receiver
            android:name="com.appsflyer.MultipleInstallBroadcastReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.android.vending.INSTALL_REFERRER" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="com.android.m6.guestlogin.model.M6_Receiver"
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

        <!-- Push notification feature in SDK -->
        <receiver
            android:name="com.vng.mb.sdk.push.GcmBroadcastReceiver"
            android:permission="com.google.android.c2dm.permission.SEND" >
            <intent-filter>

                <!-- Receives the actual messages. -->
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
                <!-- Receives the registration id(devide id). -->
                <category android:name="{your_packagename}" />
            </intent-filter>
        </receiver>
        <!-- Using Intent Service to receive new broadcast from system -->
        <service android:name="com.vng.mb.sdk.push.GCMNotificationIntentService" />

        <!-- GCM for AF log uninstall tracking -->
        <receiver
            android:name="com.google.android.gms.gcm.GcmReceiver"
            android:exported="true" >
            <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
            </intent-filter>
        </receiver>

        <!-- XuongOC -->
        <!-- NextDialTimeAlarmReceiver -->
        <receiver android:name="com.vng.mb.sdk.pushlocal.LocalPushingNotiReceiver" />
        <!-- End NextDialTimeAlarmReceiver -->
        <!-- XUongOC -->
    </application>

</manifest>


```

 + 1、请讲上述{your_packagename} 改成游戏自己的包名
 + 2、请讲上述{your_facebook_app_id}等，请联系VNG方进行获取

## VNGSEA Android 工程配置  

请在工程主AndroidManifest.xml文件中加入如下配置

```xml
  <!--VNG Permission start-->
    <permission
        android:name="{your_packagename}.permission.C2D_MESSAGE"
        android:protectionLevel="signature" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
    <uses-permission android:name="{your_packagename}.permission.C2D_MESSAGE" />
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="com.android.vending.BILLING" />
    <uses-feature
        android:name="android.hardware.camera"
        android:required="false" />
    <uses-feature
        android:name="android.hardware.camera.autofocus"
        android:required="false" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.USE_CREDENTIALS" />
    <uses-permission android:name="com.zing.zalo.permission.ACCESS_THIRD_PARTY_APP_AUTHORIZATION" />
    <uses-permission android:name="android.permission.INTERNET" />
  <!--VNG Permission end-->

  <application
        android:name="com.android.m6.guestlogin.MTOApplication"
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
		
		<!-- MAIN_ACTIVITY pls copy "intent-filter node" for schemeUrl if replace MAIN_ACTIVITY-->
		<activity
            android:name="com.tencent.imsdk.unity.vngsea.UnityPlayerNativeActivity"
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
			<!--copy “intent-filter node” for scheme url start -->
			<intent-filter>
                <data android:scheme="{your_packagename}" />
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
            </intent-filter>
			<!--copy “intent-filter node” for scheme url end  -->
        </activity>
		
		<activity 
        android:name="com.tencent.imsdk.vngsea.login.VNGSEAPermissionProxyActivity" 
        android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation" 
        android:launchMode="singleTop"
        android:theme="@android:style/Theme.Translucent.NoTitleBar"/>

		<meta-data android:name="com.tencent.imsdk.vngsea.GameVersion" android:value="v1.1.1"/>
		
		<meta-data
            android:name="appID"
            android:value="@string/appID" />
        <meta-data
            android:name="mto_game_id"
            android:value="@string/gameID" />
        <meta-data
            android:name="mto_payment_key_1"
            android:value="@string/appKey" />

        <!-- vng gameid define, can not empty & must right value -->

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
            android:value="@string/conversionID_value" />
        <meta-data
            android:name="mto_label"
            android:value="@string/conversionlable_value" />
        <meta-data
            android:name="sender_id"
            android:value="@string/sender_id" />
        <meta-data
            android:name="mto_AgeValidation"
            android:value="" />
        <meta-data
            android:name="googleWalletPubKey"
            android:value="@string/google_public_key" />
    <!-- 8487000 @integer/google_play_services_version-->
        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
        <meta-data
            android:name="com.facebook.sdk.ApplicationId"
            android:value="@string/facebook_app_id" />

        <provider
            android:name="com.facebook.FacebookContentProvider"
            android:authorities="com.facebook.app.FacebookContentProvider{your_facebook_app_id}"
            android:exported="true" />

        <activity
            android:name="vn.com.vng.fbsocial.FBActivityHandling"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        
        <!-- Get Friend list facebook  configuration -->
        <activity
            android:name="com.android.m6.guestlogin.M6_CustomFBActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        <!-- Ending of getting friend list facebook  configuration -->


        <!-- Login M6_Zalo_Login configuration -->
        
        <activity
            android:name="com.android.m6.guestlogin.ui.ZaloAutoLoginActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" >
        </activity>
        
        <activity
            android:name="com.zing.zalo.zalosdk.payment.direct.PaymentGatewayActivity"
            android:configChanges="orientation|keyboardHidden|screenSize"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>


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
            android:name="com.android.m6.guestlogin.RequestRunTimePermissionActivity"
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
        
        <activity
            android:name="com.google.android.gms.auth.api.signin.internal.SignInHubActivity"
            android:screenOrientation="sensorLandscape"
            android:windowSoftInputMode="stateAlwaysHidden|adjustPan"
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

                <category android:name="{your_packagename}" />
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

        <!-- NextDialTimeAlarmReceiver -->
        <receiver android:name="com.vng.sea.sdk.pushlocal.LocalPushingNotiReceiver" />
        <!-- End NextDialTimeAlarmReceiver -->
    <!--VNG end-->
    </application>

</manifest>


```

 + 1、请讲上述{your_packagename} 改成游戏自己的包名
 + 2、请讲上述{your_facebook_app_id}等，请联系VNG方进行获取
