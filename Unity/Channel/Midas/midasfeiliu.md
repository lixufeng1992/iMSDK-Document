## 6.4.2.1 MidasGoogle 工程配置

### MidasGoogle配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同（），

* MidasGoogle权限配置，在AndroidManifest.xml中新增一下权限

  ```xml
 <?xml version="1.0" encoding="utf-8"?> <manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.tencent.imsdk.your.packagename" android:versionCode="1" android:versionName="1.0" > <uses-permission android:name="android.permission.INTERNET" /> <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /> <uses-permission android:name="android.permission.READ_PHONE_STATE" /> <uses-permission android:name="android.permission.READ_LOGS" /> <uses-permission android:name="android.permission.GET_ACCOUNTS" /> <uses-permission android:name="android.permission.USE_CREDENTIALS" /> <uses-permission android:name="com.android.vending.BILLING" /> <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/> <uses-permission android:name="android.permission.READ_PHONE_STATE"/> <uses-permission android:name="android.permission.RECEIVE_SMS" /> <!-- Midas common activity begin --> <activity android:name="com.feiliu.gameplatform.FLGooglePlayActivity" /> <activity android:name="com.feiliu.gameplatform.popwindow.FLSdkActivity" android:configChanges="orientation|keyboardHidden|screenSize" android:label="" android:theme="@android:style/Theme.Light.NoTitleBar.Fullscreen" /> <meta-data android:name="FL_PARTNER_KEY" android:value="A3D5B4B2-A5A4-33D0-87DA-EEF242B36CE7" /> <meta-data android:name="FLGAMESDK_APP_ID" android:value="200011" /> <meta-data android:name="FLGAMESDK_COMPANY_ID" android:value="200005" /> <meta-data android:name="FLGAMESDK_COOP_ID" android:value="400001" /> <!-- 以下用于T-STORE --> <meta-data android:name="iap:api_version" android:value="3" /> <!-- 以上用于T-STORE --> <!-- 以下用于谷歌游戏登陆 --> <meta-data android:name="com.google.android.gms.games.APP_ID" android:value="913607586886" /> <meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" /> <!-- 支付Activity start --> <activity android:name="com.tencent.midas.oversea.business.APMallActivity" android:configChanges="keyboard|keyboardHidden" android:theme="@android:style/Theme.NoTitleBar.Fullscreen" > </activity> <activity android:name="com.tencent.midas.oversea.business.APProxyMallActivity" android:configChanges="keyboard|keyboardHidden|orientation|screenSize" android:theme="@android:style/Theme.Translucent.NoTitleBar" > </activity> <!-- 支付Activity end --> </manifest> 
  
  ```

* MidasGoogle Activity 配置，在Application节点中添加如下activity配置

  ```xml

   <!--=======================Midas通用Activity start==========================-->

        <activity

            android:name="com.tencent.midas.oversea.business.APMallActivity"

            android:screenOrientation="landscape"

            android:configChanges="keyboard|keyboardHidden|screenSize|orientation"

            android:theme="@android:style/Theme.NoTitleBar.Fullscreen">

        </activity>

        <activity

            android:name="com.tencent.midas.oversea.business.APProxyMallActivity"

            android:screenOrientation="landscape"

            android:configChanges="keyboard|keyboardHidden|screenSize|orientation"

            android:theme="@android:style/Theme.Translucent.NoTitleBar">

        </activity>  

    <!--=======================Midas通用Activity end==========================-->

    <!--======================MidasGoogle Activity start=========================-->

            <!--无Activity-->

    <!--======================MidasGoogle Activity end===========================-->

  ```

  

### MidasGoogle代码实例

* 与[米大师支付](../../Module/pay-midas.md)文档一致，请参见文档