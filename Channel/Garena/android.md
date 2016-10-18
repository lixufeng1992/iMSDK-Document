\# 6.4.1 Garena\(Android\) 工程配置

\#\# Android工程通用配置

注意：Garena Android 的配置可以参考文档：\[http:\/\/developer.garena.com\/docs\/msdk\/android\/getting\/started\]\(http:\/\/developer.garena.com\/docs\/msdk\/android\/getting\/started\)

1. 权限，分为必选权限和可选项权限

 - 必选权限

 

 \`\`\`xml

 &lt;uses-permission android:name="android.permission.INTERNET" \/&gt;

 &lt;uses-permission android:name="com.android.vending.BILLING" \/&gt;

 &lt;uses-permission android:name="android.permission.READ\_LOGS" \/&gt;

 &lt;uses-permission android:name="android.permission.WAKE\_LOCK" \/&gt;

 &lt;uses-permission android:name="android.permission.WRITE\_EXTERNAL\_STORAGE" \/&gt;

 &lt;uses-permission android:name="android.permission.ACCESS\_NETWORK\_STATE" \/&gt;

 &lt;uses-permission android:name="android.permission.READ\_PHONE\_STATE" \/&gt;

 \`\`\`

 - 可选权限

 无可选权限

2. 配置

 - ID 配置，该配置项由 Garena 提供，并且测试环境和正式环境不一样

 

 \`\`\`xml

 &lt;meta-data android:name="com.garena.sdk.applicationId" android:value="1000??" \/&gt;

 &lt;meta-data android:name="com.tencent.imsdk.garena.APP\_SDK\_KEY"

 android:value="49c1b7af60b1f5xxxxxxxx" \/&gt;

 &lt;meta-data android:name="com.garena.sdk.ApplicationSourceId" android:value="2" \/&gt;

 \`\`\`

 &gt; 其中:&lt;br&gt;

 &gt; applicationId 为纯数字;&lt;br&gt;

 &gt; APP SDK KEY为字符串;&lt;br&gt;

 &gt; ApplicationSourceId 为渠道 ID，需要根据发布渠道进行区分：2 为 Google 发布渠道，2000 为 Garena 发布渠道

 - 环境配置，分为正式环境\("test"\)和测试环境\("production"\)

 

 \`\`\`xml

 &lt;meta-data android:name="com.tencent.imsdk.garena.Environment" android:value="test" &gt;

 \`\`\`

 - 推送 ID 配置

 

 \`\`\`xml

 &lt;meta-data android:name="com.garena.sdk.push.applicationId" android:value="1000??" \/&gt;

 \`\`\`

 &gt; 一般与应用ID（applicationId）一致

 - BeeTalk 登录 Activity 配置

 \`\`\`xml

 &lt;activity

 android:name="com.beetalk.sdk.BTLoginActivity"

 android:screenOrientation="portrait"

 android:theme="@android:style\/Theme.Translucent.NoTitleBar.Fullscreen" \/&gt;

 &lt;activity

 android:name="com.beetalk.sdk.BTBeeTalkAuthActivity"

 android:screenOrientation="portrait" \/&gt;

 &lt;activity

 android:name="com.beetalk.sdk.plugin.GGPluginActivity"

 android:configChanges="orientation\|screenSize"

 android:screenOrientation="portrait"

 android:theme="@android:style\/Theme.Translucent.NoTitleBar.Fullscreen" \/&gt;

 \`\`\`

 - BeeTalk 支付 Activity 配置

 

 \`\`\`xml

 &lt;activity android:name="com.garena.pay.android.GGPayActivity"

 android:configChanges="orientation"

 android:exported="true"

 android:launchMode="singleTop"

 android:screenOrientation="portrait"

 android:theme="@style\/Theme.Transparent" \/&gt;

 \`\`\`

 

 - BeeTalk 统计上报地址，该配置项由 Garena 提供

 \`\`\`xml

 &lt;meta-data android:name="com.beetalklib.ganalytics.report\_url" android:value="http:\/\/xxx.xxx.xxx.xxx:xxxx" \/&gt;

 \`\`\`

 

 - Garena 登录 Activity 配置

 \`\`\`xml

 &lt;activity

 android:name="com.beetalk.sdk.GarenaAuthActivity"

 android:screenOrientation="portrait" \/&gt;

 \`\`\`

 

 - Garena 内置了 Facebook 登陆，需要添加如下 Facebook 配置

 

 \* App ID 配置

 

 \`\`\`xml

 &lt;meta-data

 android:name="com.facebook.sdk.ApplicationId"

 android:value="\ 427??????????" \/&gt;

 \`\`\`

 &gt; 注意：这里的 Facebook App ID 需要以 string 字符串的格式填充，直接填写需在前面添加“\\"和空格

 

 \* Facebook Activity 配置

 

 \`\`\`xml

 &lt;activity android:name="com.facebook.FacebookActivity"

 android:configChanges="keyboard\|keyboardHidden\|screenLayout\|screenSize\|orientation"

 android:theme="@android:style\/Theme.Translucent.NoTitleBar"

 android:label="@string\/app\_name" \/&gt;

 \`\`\`

 

 \* 如果需要使用 Facebook 的图片、视频等多媒体分享功能，还需要添加如下配置

 

 \`\`\`xml

 &lt;provider

 android:authorities="com.facebook.app.FacebookContentProvider\[Facebook App ID\]"

 android:name="com.facebook.FacebookContentProvider"

 android:exported="true" \/&gt;

 \`\`\`

 

 &gt; 其中，\[Facebook App ID\] 需要替换成应用的 Facebook ID

 

 - Garena 推送配置

 

 \* Receiver 配置

 \`\`\`xml

 &lt;receiver android:name="com.garena.android.gpns.logic.AlarmReceiver"

 android:process="com.garena.msdk.pushservice2" &gt;

 &lt;intent-filter&gt;

 &lt;action android:name="com.garena.android.gpns.ALARM\_ACTION1000??" \/&gt;

 &lt;\/intent-filter&gt;

 &lt;\/receiver&gt;

 &lt;receiver

 android:name="com.garena.android.DefaultNotificationReceiver"

 android:enabled="true"

 android:exported="true" &gt;

 &lt;intent-filter&gt;

 &lt;action android:name="com.garena.android.gpns.NOTIFICATION\_RECEIVE" \/&gt;

 &lt;category android:name="com.garena.garena\_msdk\_sample.app" \/&gt;

 &lt;\/intent-filter&gt;

 &lt;\/receiver&gt;

 \`\`\`

 &gt; 其中，intent-filter 的值最后续加上 Application ID，如：

 \`\`\`xml

 &lt;action android:name="com.garena.android.gpns.ALARM\_ACTION100010" \/&gt;

 \`\`\`

 &gt; com.garena.garena\_msdk\_sample.app 需要修改成游戏包名

 

 \* Service 配置

 

 \`\`\`xml

 &lt;service android:name="com.garena.android.gpns.GNotificationService"

 android:enabled="true"

 android:exported="true"

 android:process="com.garena.msdk.pushservice2" &gt;

 &lt;intent-filter&gt;

 &lt;action android:name="com.garena.android.gpush.GNotificationService" \/&gt;

 &lt;\/intent-filter&gt;

 &lt;\/service&gt;

 \`\`\`

 

 \* 其他配置

 

 \`\`\`xml

 &lt;service

 android:name="com.garena.android.gpns.strategy.ServiceLoaderIntentService"

 android:exported="false" \/&gt;

 \`\`\`

 \* 卸载相关配置

 

 \`\`\`xml

 &lt;receiver

 android:name="com.garena.android.gpns.logic.UninstallReceiver"

 android:enabled="true"

 android:exported="true" &gt;

 &lt;intent-filter&gt;

 &lt;category android:name="android.intent.category.DEFAULT" \/&gt;

 &lt;action android:name="android.intent.action.PACKAGE\_REMOVED" \/&gt;

 &lt;data android:scheme="package" \/&gt;

 &lt;\/intent-filter&gt;

 &lt;\/receiver&gt;

 \`\`\`

 

 \* 重启相关

 

 \`\`\`xml

 &lt;receiver android:name="com.garena.android.gpns.logic.RebootReceiver"&gt;

 &lt;intent-filter&gt;

 &lt;action android:name="android.intent.action.BOOT\_COMPLETED"\/&gt;

 &lt;\/intent-filter&gt;

 &lt;intent-filter&gt;

 &lt;action android:name="android.intent.action.EXTERNAL\_APPLICATIONS\_AVAILABLE"\/&gt;

 &lt;\/intent-filter&gt;

 &lt;\/receiver&gt;

 \`\`\`

 

 \* 其他

 

 \`\`\`xml

 &lt;receiver

 android:name="com.garena.android.gpns.strategy.RemoteQueryReceiver"

 android:process="com.garena.msdk.pushservice3"&gt;

 &lt;intent-filter&gt;

 &lt;action android:name="com.garena.android.gpns.enquiry"\/&gt;

 &lt;\/intent-filter&gt;

 &lt;\/receiver&gt;

 \`\`\`

