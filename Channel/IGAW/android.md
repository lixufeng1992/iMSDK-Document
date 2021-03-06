### Android配置管理

* 权限配置

    请在工程主AndroidManifest.xml文件中加入如下权限配置
    + common permission
    ```xml
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    ```

    + 推送额外需要的权限
    ```xml
    <uses-permission android:name="android.permission.GET_ACCOUNTS"/>
    <uses-permission android:name="android.permission.WAKE_LOCK"/>
    <uses-permission android:name="android.permission.VIBRATE"/>
    <uses-permission android:name="android.permission.GET_TASKS"/>
    <!-- C2DM Permission -->
    <permission 
        android:name="MY_PACKAGE_NAME.permission.C2D_MESSAGE"       
        android:protectionLevel = "signature" />
    <uses-permission android:name="MY_PACKAGE_NAME.permission.C2D_MESSAGE"/>
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE"/>
    ```
    > 请将MY_PACKAGE_NAME改成游戏包名

* meta-data配置

    请在工程主AndroidManifest.xml文件中Application节点内加入以下配置
    ```xml
    <meta-data
        android:name="com.google.android.gms.version"
        android:value="@integer/google_play_services_version" />

    <!-- app key and hash key -->
    <!-- get from igaworks website -->
    <meta-data android:name="igaworks_app_key" android:value="{your app key}" />
    <meta-data android:name="igaworks_hash_key" android:value="{your hash key}" />
    ```
    > 请将{your app key} 和 {your hash key}改成游戏自己的值，该值从[IGAW官网](http://www.igaworks.com/)获得

* Receiver和Service配置

    请在工程主AndroidManifest.xml文件中Application节点内加入以下配置
    ```xml
    <receiver 
        android:name="com.igaworks.liveops.pushservice.LiveOpsGCMBroadcastReceiver"
        android:permission="com.google.android.c2dm.permission.SEND" >
    	    <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
                <category android:name="MY_PACKAGE_NAME" />
    	    </intent-filter>
    </receiver>
    <!-- IGAWorks Push Service -->
    <service 
    android:enabled="true" 
    android:name="com.igaworks.liveops.pushservice.GCMIntentService" />
    <!-- Client Push App Receiver -->
    <receiver 
        android:name="com.igaworks.liveops.pushservice.LiveOpsReceiver"
        android:permission="MY_PACKAGE_NAME.permission.C2D_MESSAGE">
        <intent-filter>
            <action android:name="com.igaworks.liveops.pushservice.CLIENT_PUSH_RECEIVE"/>
        </intent-filter>
    </receiver>
    ```
     > 请将MY_PACKAGE_NAME改成游戏包名

