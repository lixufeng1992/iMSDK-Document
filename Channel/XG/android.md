## 6.4.2 信鸽 Android工程配置

#### 1. Android工程通用配置

信鸽所需要的配置在官方文档都有详细说明，下面是必须的配置，有其他不明白的，可以参考[信鸽官方文档](http://developer.qq.com/wiki/xg/Android接入/Android%20SDK快速接入/Android%20SDK快速接入.html)

* 权限配置

  ```xml
  <!-- 【必须】 信鸽SDK所需权限 -->
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
<uses-permission android:name="android.permission.RESTART_PACKAGES" />
<uses-permission android:name="android.permission.BROADCAST_STICKY" />
<uses-permission android:name="android.permission.WRITE_SETTINGS" />
<uses-permission android:name="android.permission.RECEIVE_USER_PRESENT" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.KILL_BACKGROUND_PROCESSES" />
<uses-permission android:name="android.permission.GET_TASKS" />
<uses-permission android:name="android.permission.READ_LOGS" />
<uses-permission android:name="android.permission.VIBRATE" />
<!-- 【可选】 信鸽SDK所需权限 -->
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BATTERY_STATS" />
  ```

* Activity 配置，在Application节点中添加如下activity配置

  ```xml
    < !-- 【必须】 信鸽receiver广播接收 -->
    < receiver
        android:name="com.tencent.android.tpush.XGPushReceiver"
        android:process=":xg_service_v2" >
        < intent-filter android:priority="0x7fffffff" >
            < !-- 【必须】 信鸽SDK的内部广播 -->
            < action android:name="com.tencent.android.tpush.action.SDK" />
            < action android:name="com.tencent.android.tpush.action.INTERNAL_PUSH_MESSAGE" />
            < !-- 【必须】 系统广播：开屏和网络切换 -->
            < action android:name="android.intent.action.USER_PRESENT" />
            < action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
            < !-- 【可选】 一些常用的系统广播，增强信鸽service的复活机会，请根据需要选择。当然，你也可以添加APP自定义的一些广播让启动service -->
            < action android:name="android.bluetooth.adapter.action.STATE_CHANGED" />
            < action android:name="android.intent.action.ACTION_POWER_CONNECTED" />
            < action android:name="android.intent.action.ACTION_POWER_DISCONNECTED" />
        < /intent-filter>
    < /receiver>    

    < !-- 【必须】 (2.30及以上版新增)展示通知的activity -->
    < !-- 【注意】 如果被打开的activity是启动模式为SingleTop，SingleTask或SingleInstance，请根据通知的异常自查列表第8点处理 -->
    < activity
        android:name="com.tencent.android.tpush.XGPushActivity"
        android:exported="true" >
        < intent-filter>
            < !-- 若使用AndroidStudio，请设置android:name="android.intent.action" -->
            < action android:name="android.intent.action" />
        < /intent-filter>
    < /activity>    

    < !-- 【必须】 信鸽service -->
    < service
        android:name="com.tencent.android.tpush.service.XGPushService"
        android:exported="true"
        android:persistent="true"
        android:process=":xg_service_v2" />
    < !-- 【必须】 通知service，此选项有助于提高抵达率 -->
    < service
        android:name="com.tencent.android.tpush.rpc.XGRemoteService"
        android:exported="true" >
        < intent-filter>
            < action android:name="YOUR_PACKAGENAME.PUSH_ACTION" />
        < /intent-filter>
    < /service>
    < !-- 【必须】 请将YOUR_ACCESS_ID修改为APP的AccessId，“21”开头的10位数字，中间没空格 -->
    < meta-data
        android:name="XG_V2_ACCESS_ID"
        android:value="YOUR_ACCESS_ID" />
    < !-- 【必须】 请将YOUR_ACCESS_KEY修改为APP的AccessKey，“A”开头的12位字符串，中间没空格 -->
    < meta-data
        android:name="XG_V2_ACCESS_KEY"
        android:value="YOUR_ACCESS_KEY" />
    < !-- APP实现的Receiver,用于接收消息和结果反馈 -->
    < receiver android:name="com.tencent.imsdk.push.xg.IMXGPushReceiver" >
        < intent-filter>
            < !-- 接收消息透传 -->
            < action android:name="com.tencent.android.tpush.action.PUSH_MESSAGE" />
            < !-- 监听注册、反注册、设置/删除标签、通知被掉级等处理结果 -->
            < action android:name="com.tencent.android.tpush.action.FEEDBACK" />
        < /intent-filter>
    < /receiver>
  ```

  > 注意替换YOUR_PACKAGENAME、YOUR_ACCESS_ID和YOUR_ACCESS_KEY, [请参考信鸽开发者中心配置](developer.md) <br>
  > 并且数字需要写成"\\ 123456"这种模式，"\\"和空格不能少

