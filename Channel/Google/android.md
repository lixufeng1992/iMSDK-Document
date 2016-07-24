## 6.2.2 Android工程配置

### Android工程通用配置

* 权限配置，在AndroidManifest.xml中新增网络访问权限

  ```xml
  <uses-permission android:name="android.permission.INTERNET"/>
  ```

* GMS版本配置，在Application节点中添加如下配置：

 ```xml
 <meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
 ```

 > 默认情况下，value值无需修改。如果采用非iMSDK提供的GMS版本，可以根据版本号修改对应的值

* 应用ID配置

  ```xml
 <meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ 263738040849" />
 <meta-data android:name="com.google.android.gms.serverclientid"
 android:value="263738040849-kgcholbfoi8163lpn8ke3l3dsc3pvtu4.apps.googleusercontent.com" />
  ```




