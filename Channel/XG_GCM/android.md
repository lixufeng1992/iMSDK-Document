## 信鸽 Android工程配置

#### 1. Android工程通用配置

* 权限配置

  ```xml
    <!-- 【必须】 信鸽SDK所需权限 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.WRITE_SETTINGS" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.VIBRATE" />
    <!-- 【常用】 信鸽SDK所需权限 -->
    <uses-permission android:name="android.permission.RECEIVE_USER_PRESENT" />
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <!-- 【可选】 信鸽SDK所需权限 -->
    <uses-permission android:name="android.permission.RESTART_PACKAGES" />
    <uses-permission android:name="android.permission.BROADCAST_STICKY" />
    <uses-permission android:name="android.permission.KILL_BACKGROUND_PROCESSES" />
    <uses-permission android:name="android.permission.GET_TASKS" />
    <uses-permission android:name="android.permission.READ_LOGS" />
    <uses-permission android:name="android.permission.BLUETOOTH" />
    <uses-permission android:name="android.permission.BATTERY_STATS" />

    <!-- [START gcm_permission] -->
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    <!-- 声明并使用一个自定义的权限以此来确保只有这个程序可以接收你的GCM消息, 如果是4.1或更高版本的系统就不需要这个权限 -->
    <permission
        android:name="{YOUR_PACKAGENAME}.permission.C2D_MESSAGE"
        android:protectionLevel="signature" />

    <uses-permission android:name="{YOUR_PACKAGENAME}.permission.C2D_MESSAGE" />
  ```

* Activity 配置，在Application节点中添加如下activity配置

  ```xml
    <!-- 【必须】 (2.30及以上版新增)展示通知的activity -->
     <activity
         android:name="com.tencent.android.tpush.XGPushActivity"
         android:exported="false"
         android:theme="@android:style/Theme.Translucent" >
         <intent-filter>

             <!-- 若使用AndroidStudio，请设置android:name="android.intent.action" -->
             <action android:name="android.intent.action" />
         </intent-filter>
     </activity>

     <!-- 【必须】 信鸽receiver广播接收 -->
     <receiver
         android:name="com.tencent.android.tpush.XGPushReceiver"
         android:process=":xg_service_v2" >
         <intent-filter android:priority="0x7fffffff" >

             <!-- 【必须】 信鸽SDK的内部广播 -->
             <action android:name="com.tencent.android.tpush.action.SDK" />
             <action android:name="com.tencent.android.tpush.action.INTERNAL_PUSH_MESSAGE" />
             <!-- 【必须】 系统广播：网络切换 -->
             <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />

             <!-- 【可选】 系统广播：开屏 -->
             <action android:name="android.intent.action.USER_PRESENT" />

             <!-- 【可选】 一些常用的系统广播，增强信鸽service的复活机会，请根据需要选择。当然，你也可以添加APP自定义的一些广播让启动service -->
             <action android:name="android.bluetooth.adapter.action.STATE_CHANGED" />
             <action android:name="android.intent.action.ACTION_POWER_CONNECTED" />
             <action android:name="android.intent.action.ACTION_POWER_DISCONNECTED" />
         </intent-filter>
         <!-- 【可选】 usb相关的系统广播，增强信鸽service的复活机会，请根据需要添加 -->
         <intent-filter android:priority="0x7fffffff" >
             <action android:name="android.intent.action.MEDIA_UNMOUNTED" />
             <action android:name="android.intent.action.MEDIA_REMOVED" />
             <action android:name="android.intent.action.MEDIA_CHECKING" />
             <action android:name="android.intent.action.MEDIA_EJECT" />

             <data android:scheme="file" />
         </intent-filter>
     </receiver>
     <!-- 【必须】 信鸽service -->
     <service
         android:name="com.tencent.android.tpush.service.XGPushService"
         android:exported="true"
         android:persistent="true"
         android:process=":xg_service_v2" />

     <!-- 【必须】 通知service，其中android:name部分要改为当前包名 -->
     <service
         android:name="com.tencent.android.tpush.rpc.XGRemoteService"
         android:exported="true" >
         <intent-filter>

             <!-- 【必须】 请修改为当前APP名包.PUSH_ACTION，如demo的包名为：com.tencent.imsdk.samples -->
             <action android:name="{YOUR_PACKAGENAME}.PUSH_ACTION" />
         </intent-filter>
     </service>

     <!-- 【可选】APP实现的Receiver，用于接收消息透传和操作结果的回调，请根据需要添加 -->
     <!-- YOUR_PACKAGE_PATH.CustomPushReceiver需要改为自己的Receiver： -->
     <!-- com.tencent.imsdk.push.xg.IMXGPushReceiver是IMSDK默认接收器 -->
     <receiver
         android:name="com.tencent.imsdk.push.xg.IMXGPushReceiver"
         android:exported="false" >
         <intent-filter>
             <!-- 接收消息透传 -->
             <action android:name="com.tencent.android.tpush.action.PUSH_MESSAGE" />
             <!-- 监听注册、反注册、设置/删除标签、通知被点击等处理结果 -->
             <action android:name="com.tencent.android.tpush.action.FEEDBACK" />
         </intent-filter>
     </receiver>

     <!-- [START gcm_receiver] -->
     <receiver
         android:name="com.google.android.gms.gcm.GcmReceiver"
         android:exported="true"
         android:permission="com.google.android.c2dm.permission.SEND" >
         <intent-filter>
             <action android:name="com.google.android.c2dm.intent.RECEIVE" />
             <action android:name="com.google.android.c2dm.intent.REGISTRATION" />
             <!-- 下面修改为应用的包名 -->
             <category android:name="{YOUR_PACKAGENAME}" />
         </intent-filter>
     </receiver>
     <!-- [END gcm_receiver] -->
     <!-- [START gcm_listener] -->
     <service
         android:name="com.tencent.android.gcm.XGGcmListenerService"
         android:exported="false" >
         <intent-filter>
             <action android:name="com.google.android.c2dm.intent.RECEIVE" />
         </intent-filter>
     </service>
     <!-- [END gcm_listener] -->
     <!-- [START instanceId_listener] -->
     <service
         android:name="com.tencent.android.gcm.XGGcmInstanceIDListenerService"
         android:exported="false" >
         <intent-filter>
             <action android:name="com.google.android.gms.iid.InstanceID" />
         </intent-filter>
     </service>
     <!-- 不加这个isGooglePlayServicesAvailable出问题， 8115000是google-play-services.jar的版本，要求手机上的google play service版本大于此值 -->
     <meta-data
         android:name="com.google.android.gms.version"
         android:value="@integer/google_play_services_version" />
     <!-- [END instanceId_listener] -->
     <!-- 【必须】 请修改为APP的AccessId，“21”开头的10位数字，中间没空格 -->
     <meta-data
         android:name="XG_V2_ACCESS_ID"
         android:value="{YOUR_ACCESS_ID}" />
     <!-- 【必须】 请修改为APP的AccessKey，“A”开头的12位字符串，中间没空格 -->
     <meta-data
         android:name="XG_V2_ACCESS_KEY"
         android:value="{YOUR_ACCESS_KEY}" />

     <!-- 【可选】不配置GCM的SENDER ID，xg gcm 功能不起作用,纯数字必须在前面加前缀 ： '\ ' -->
     <meta-data
         android:name="GCM_SENDER_ID"
         android:value="{YOUR_SENDER_ID}" />
  ```

  > 注意替换YOUR_PACKAGENAME、YOUR_ACCESS_ID、YOUR_ACCESS_KEY和YOUR_SENDER_ID, [请参考信鸽开发者中心配置](../XG/developer.md) 以及 [信鸽GCM开发者中心配置](developer.md)<br>
  > 并且数字需要写成"\\ 123456"这种模式，"\\"和空格不能少

#### [推送模块详细使用说明 (Push)](../../Unity/Module/push.md)

