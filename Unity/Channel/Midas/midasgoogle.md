<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.tencent.imsdk.your.packagename"
    android:versionCode="1"
    android:versionName="1.0" >
    <!--================Midas通用权限 start==========================-->
     <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <!--===============Midas通用权限 end=============================-->

    <!--==================MdiasGoogle 权限start========================-->
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="com.android.vending.BILLING" />
    <!--==================MdiasGoogle 权限end=========================-->

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
            <!--无-->
    <!--======================MidasGoogle Activity end===========================-->
    </manifest>