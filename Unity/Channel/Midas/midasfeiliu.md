## 6.4.2.1 MidasGoogle 工程配置

### MidasGoogle配置

Midas支付分为Midas内核包及Midas插件包，其中插件包配置依据插件本身的要求而各有不同（），

* MidasGoogle权限配置，在AndroidManifest.xml中新增一下权限

  ```xml

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