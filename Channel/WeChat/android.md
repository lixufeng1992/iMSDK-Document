### Android 配置


* 权限配置，在AndroidManifest.xml中新增权限

 ```xml
 <uses-permission android:name="android.permission.INTERNET"/>
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
 <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
 <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
 ```

* 入口Activity配置，在Application节点中添加如下activity配置

 ```xml
 <activity android:name="com.tencent.imsdk.sns.wxapi.WXEntryActivity"
 android:exported="true"
 android:theme="@android:style/Theme.NoDisplay" />
 <activity-alias android:name=".wxapi.WXEntryActivity"
 android:exported="true"
 android:targetActivity="com.tencent.imsdk.sns.wxapi.WXEntryActivity"/>
 ```

* App Id 配置，在Application节点中添加如下配置

 ```xml
 <meta-data android:name="com.tencent.imsdk.WechatAppId" android:value="{your wechat appid}"/>
 ```

 需要将value值修改为业务自己的App ID

