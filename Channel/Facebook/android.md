## 6.1.1.2 Android 工程配置

### Android工程通用配置

Facebook所需要的配置都官方文档都有详细说明，请参考：[https://developers.facebook.com/docs/android/getting-started/](https://developers.facebook.com/docs/android/getting-started/)

* 权限配置，在AndroidManifest.xml中新增网络访问权限

  ```xml
  <uses-permission android:name="android.permission.INTERNET"/>
  ```

* Activity 配置，在Application节点中添加如下activity配置

  ```xml
  <activity android:name="com.facebook.FacebookActivity"
          android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation"
          android:theme="@android:style/Theme.Translucent.NoTitleBar"
          android:label="@string/app_name" />
  ```

* App Id 配置，在Application节点中添加如下配置，其中值为字符串类型

  ```xml
  <meta-data android:name="com.facebook.sdk.ApplicationId" android:value="\ 123456"/>
  ```

  需要将value值修改为业务自己的App ID
  
  > 注意：需要写成"\\ 123456"这种模式，"\\"和空格不能少

### 分享及好友模块配置

如果使用分享及好友模块，需要增加如下配置：

* 完成Faceboook通用配置
  
* provider配置，在Application节点下，添加如下provider配置

  ```xml
  <provider android:authorities="com.facebook.app.FacebookContentProvider423362744481374" 
      android:name="com.facebook.FacebookContentProvider" 
      android:exported="true"/>
  ```
  
  其中，423362744481374这串数字需要改成游戏自己的App ID

