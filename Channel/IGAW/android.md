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
