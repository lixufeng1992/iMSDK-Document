###　Appang统计配置说明

####　Android端配置说明

* 权限配置

    请在工程主AndroidManifest.xml文件中添加如下权限配置
```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.READ_PHONE_STATE"/> 
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
```

* meta-data配置

    请在工程主AndroidManifest.xml文件中Application节点内添加如下meta-data配置
```xml
<meta-data android:name="APPANG_AD_KEY" android:value="your key value" />
```