## 6.8.2 

Kakao的工程配置需要，官方文档地址为：[https://gamecenter.kakao.com/docs/documents/281](https://gamecenter.kakao.com/docs/documents/281)

* 权限配置，在 AndroidManifest.xml 中新增如下访问权限：

 ```xml
 <!-- 1. Setup the network auth to communicate with the server. -->
 <uses-permission android:name="android.permission.INTERNET" />
 <!-- Auth to access the SD card is needed to cache images. -->
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
 ```

* 入口 Application 配置

 Kakao 需要抢占入口 Application，在 Unity 的 Assets/Plugins/Android/AndroidManifest.xml 中，找到入口 Application 节点，并添加 name 属性：

 ```xml
 <application android:name="com.tencent.imsdk.unity.kakao.GlobalApplication"
 android:theme="@android:style/Theme.NoTitleBar"
 android:icon="@drawable/app_icon"
 android:label="@string/app_name"
 android:debuggable="true">
 ```
* Native App ID 配置，在 AndroidManifest.xml 的 Application 节点下，添加如下配置

 ```xml
 <meta-data android:name="com.kakao.sdk.AppKey"
 android:value="217ac19097ef33c997bxxxxxxxxxxxxx" />
 ```

 其中，217ac19097ef33c997bxxxxxxxxxxxxx 需要替换成游戏自己的 native app id

* Activity filter 配置，在需要调用 Kakao 的 Activity 中，增加如下配置

 ```xml
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 <category android:name="android.intent.category.DEFAULT" />
 <category android:name="android.intent.category.BROWSABLE" />
 <data android:scheme="kakao217ac19097ef33c997bxxxxxxxxxxxxx" />
 </intent-filter>
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 <category android:name="android.intent.category.DEFAULT" />
 <category android:name="android.intent.category.BROWSABLE" />
 <data android:scheme="kakao217ac19097ef33c997bxxxxxxxxxxxxx" android:host="kakaolink" />
 </intent-filter>
 <intent-filter>
 <action android:name="android.intent.action.VIEW" />
 <category android:name="android.intent.category.DEFAULT" />
 <category android:name="android.intent.category.BROWSABLE" />
 <data android:scheme="kakao217ac19097ef33c997bxxxxxxxxxxxxx" android:host="kakaostory" />
 </intent-filter>
 ```

 其中，217ac19097ef33c997bxxxxxxxxxxxxx 需要替换成游戏自己的 native app id

 > 一般，Unity 的 Activity 一般为 com.unity3d.player.UnityPlayerNativeActivity， 如果没有该节点，则固定为带有如下子节点 Activity，
 ```xml
 <action android:name="android.intent.action.MAIN"/>
 <category android:name="android.intent.category.LAUNCHER"/>
 <category android:name="android.intent.category.LEANBACK_LAUNCHER"/>
 ```