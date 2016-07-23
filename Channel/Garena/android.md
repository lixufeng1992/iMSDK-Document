## 6.4.1 Midas(Android) 工程配置

### Android工程通用配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同,详情见[Midas配置](../midas.md)，

* Midas内核包权限配置，在AndroidManifest.xml中新增一下权限

 ```xml
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 ```

* Midas内核包Activity 配置，在Application节点中添加如下activity配置

 ```xml
 <activity
 android:name="com.tencent.midas.oversea.business.APMallActivity"
 android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
 android:screenOrientation="sensorLandscape"
 android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
 </activity>
 <activity
 android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
 android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
 android:screenOrientation="sensorLandscape"
 android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>
 ```