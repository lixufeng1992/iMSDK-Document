## 6.3.2 Expansion Android工程配置

#### 1. Android工程通用配置

* 权限配置

  ```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WAKE_LOCK"/>
<uses-permission android:name="com.android.vending.CHECK_LICENSE" />
  ```

* Activity 配置，在Application节点中添加如下service配置

  ```xml
    < service android:name="com.tencent.imsdk.expansion.downloader.impl.DownloaderService" android:exported = "false"/>
  ```

#### 2. [Expansion 模块详细使用说明](../../Unity/Module/obb.md)