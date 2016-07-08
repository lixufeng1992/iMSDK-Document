## 6.4.2 XG Android 工程配置

#### 1. Android工程通用配置

XG所需要的配置在官方文档都有详细说明，下面是必须的配置，有其他不明白的，可以参考[信鸽官方文档](http://developer.qq.com/wiki/xg/Android接入/Android%20SDK快速接入/Android%20SDK快速接入.html)

* 权限配置

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

#### 2. 分享及好友模块配置

如果使用分享及好友模块，需要增加如下配置：

* 完成Faceboook通用配置
  
* provider配置，在Application节点下，添加如下provider配置

  ```xml
  <provider android:authorities="com.facebook.app.FacebookContentProvider423362744481374" 
      android:name="com.facebook.FacebookContentProvider" 
      android:exported="true"/>
  ```
  
  其中，423362744481374这串数字需要改成游戏自己的App ID