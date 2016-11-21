###　Appang统计配置说明

####　Android端配置说明

* 权限配置

    请在工程主AndroidManifest.xml文件中添加如下权限配置
```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.READ_PHONE_STATE"/> 
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
```

* 请在 ```<Application />``` 节点中添加如下 meta-data配置

    请在工程主AndroidManifest.xml文件中Application节点内添加如下meta-data配置
```xml
<!--for example : <meta-data android:name="APPANG_AD_KEY" android:value="12a34b56xxxxxxxxxxxxxxxxxxxxxxxx" /> -->
<meta-data android:name="APPANG_AD_KEY" android:value="your key value" />
```
    > 上述APPANG_AD_KEY值请到[Appang官网](http://www.appang.kr/home/)申请 或运营方提供

    > android.permission.READ_PHONE_STATE  用于获取设备ID