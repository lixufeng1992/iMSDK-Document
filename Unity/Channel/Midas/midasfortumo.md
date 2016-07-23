## 6.4.2.1 MidasGoogle 工程配置

### MidasGoogle配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

* MidasGoogle权限配置，在AndroidManifest.xml中新增一下权限

 ```xml
 <!--通用权限-->
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

 <!--Fortumo支付需要的权限-->
 <uses-permission android:name="android.permission.RECEIVE_SMS" />
 <uses-permission android:name="android.permission.SEND_SMS" />
 <!--Fortumo支付自定义权限，XXXX部分请定义为您自己的包名
 从Android L开始，signature的自定义权限需要签名相同。
 <permission android:name="XXXX.permission.PAYMENT_BROADCAST_PERMISSION" --> 
 <permission android:name="[your_package_name].permission.PAYMENT_BROADCAST_PERMISSION"
     android:label="Read payment status"
     android:protectionLevel="signature" />
 <!-- "signature" permission granted automatically by system, without notifying user. -->
 <uses-permission android:name="[your_package_name].permission.PAYMENT_BROADCAST_PERMISSION" />
 ```

* MidasGoogle Activity 配置，在Application节点中添加如下activity配置

 ```xml
 <!-- midas fortumo start -->
 <!--midas通用Activity-->
 <activity
 android:name="com.tencent.midas.oversea.business.APMallActivity"
 android:screenOrientation="sensorLandscape"
 android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
 android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
 </activity>
 <activity
 android:name="com.tencent.midas.oversea.business.APProxyMallActivity"
 android:screenOrientation="sensorLandscape"
 android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
 android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>

 <!--Fortumo专用-->
 <activity
 android:name="com.tencent.midas.oversea.business.payhub.fortumo.APProxyActivity"
 android:screenOrientation="sensorLandscape"
 android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
 android:theme="@android:style/Theme.Translucent.NoTitleBar">
 </activity>
 <receiver android:name="mp.MpSMSReceiver">
 <intent-filter>
 <action android:name="android.provider.Telephony.SMS_RECEIVED" />
 </intent-filter>
 </receiver>
 <service android:name="mp.MpService" />
 <service android:name="mp.StatusUpdateService" />
 <activity android:name="mp.MpActivity"
 android:theme="@android:style/Theme.Translucent.NoTitleBar"
 android:configChanges="orientation|keyboardHidden|screenSize" />
 <!-- 实现自己的广播类来监听Fortumo的支付状态,需要 "signature" permission -->
 <receiver android:name="com.tencent.imsdk.pay.midasfortumo.FortumoPaymentStatusReceiver"
 android:permission="com.tencent.midas.oversea.permission.PAYMENT_BROADCAST_PERMISSION">
 <intent-filter>
 <action android:name="mp.info.PAYMENT_STATUS_CHANGED" />
 </intent-filter>
 </receiver>
 <!-- midas fortumo end -->
 ```

### MidasGoogle代码实例

* 与[米大师支付](../../Module/pay-midas.md)文档一致，请参见文档