##  MidasGarena 工程配置

### MidasGarena配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasGarena 权限配置，在AndroidManifest.xml中新增一下权限

  ```xml

  <!--Midas通用权限-->
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

 <!-- Midas common activity begin -->
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

 <meta-data
     android:name="MIDAS.APP_SDK_ASSIGN_ID"
     android:value="\ 100051" />
 <meta-data
     android:name="MIDAS.VIRTUAL_CURRENCY_NAME"
     android:value="Diamond" />
 <!-- Midas end -->

  ```

  

###  MidasGarena 代码实例

* 与[米大师支付](../../Module/pay-midas.md)文档一致，请参见文档

