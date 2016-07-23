## 6.4.2.8 MidasMOL 工程配置

###  MidasMOL 配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同。

*  MidasMOL 权限配置，在AndroidManifest.xml中新增一下权限

  ```xml
 <!--通用权限--> <uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> 
<uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /> 
<!--MOL支付需要的权限--> 
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/> 
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
<uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
<uses-permission android:name="android.permission.WRITE_SETTINGS" />
<uses-permission android:name="com.android.launcher.permission.READ_SETTINGS" /> 
<uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
<uses-permission android:name="android.permission.SEND_SMS"/>

  ```

*  MidasMOL Activity 配置，在Application节点中添加如下activity配置

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

  

###  MidasMOL 代码实例

* 与[米大师支付](../../Module/pay-midas.md)文档一致，请参见文档