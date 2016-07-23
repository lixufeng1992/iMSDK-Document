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
 从Android L开始，signature的自定义权限需要签名相同。 --> 
 <permission android:name="XXXX.permission.PAYMENT_BROADCAST_PERMISSION"
 <permission android:name="[your_package_name].permission.PAYMENT_BROADCAST_PERMISSION"
     android:label="Read payment status"
     android:protectionLevel="signature" />
 <!-- "signature" permission granted automatically by system, without notifying user. -->
 <uses-permission android:name="[your_package_name].permission.PAYMENT_BROADCAST_PERMISSION" />
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