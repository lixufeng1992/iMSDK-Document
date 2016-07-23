## 6.4.2.9  MidasLink 工程配置

###   MidasLink 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*   MidasLink 权限配置，在AndroidManifest.xml中新增一下权限

```xml
<!-- Midas通用权限 -->
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<!-- 以下を追加：ここから -->
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="com.android.vending.BILLING" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission
     android:name="android.permission.READ_EXTERNAL_STORAGE"
     android:maxSdkVersion="18" />
<activity
     android:name="com.tencent.midas.oversea.business.APMallActivity"
     android:screenOrientation="landscape"
     android:configChanges="keyboard|keyboardHidden"
     android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
</activity>
<activity
     android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
     android:screenOrientation="landscape"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Translucent.NoTitleBar">
</activity>
<activity
     android:name="com.tencent.midas.oversea.business.payhub.link.APProxyActivity"
     android:screenOrientation="landscape"
     android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
     android:theme="@android:style/Theme.Translucent.NoTitleBar">
</activity>
<meta-data
     android:name="com.google.android.gms.version"
     android:value="@integer/google_play_services_version" />
<meta-data
     android:name="com.aiming.link.purchase.Base64PublicKey"
     android:value="your Bse64PublicKey" />
<meta-data
     android:name="com.aiming.link.purchase.ItemDisplayName"
     android:value="your ItemDisplayName" />

 ```

###  MidasLink 代码实例

* 与[米大师支付](../../Module/pay-midas.md) 一致
