## 6.4.2.7 MidasBoku 工程配置

###  MidasBoku配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasBoku在AndroidManifest.xml中新增以下配置

```xml
 <!--================Midas通用权限 start==========================-->
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
 <!--===============Midas通用权限 end=============================-->
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
 <!--======================MidasBoku Activity start=========================-->
 <activity
 android:name="com.tencent.midas.oversea.business.payhub.boku.APBokuWebActivity"
 android:configChanges="keyboard|keyboardHidden"
 android:theme="@android:style/Theme.NoTitleBar.Fullscreen" />
 <!--======================MidasBoku Activity end===========================-->
 ```

  

###  MidasBoku代码实例

* 与[米大师支付](../../Module/pay-midas.md)文档一致，请参见文档