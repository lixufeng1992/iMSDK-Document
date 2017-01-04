# Adjust(iOS)配置说明

##IMSDK配置
配置文件**IMSDKAppSetting.bundle/Contents/Resources/app.plist**添加配置项`Appsflyer`

```
<key>Adjust</key>
	<dict>
		<key>appid</key>
		<string>YOUR_APP_ID</string>
		<key>appkey</key>
		<string>YOUR_APP_KEY</string>
	</dict>
```

##添加系统库依赖

+ libz.tbd
+ libsqlite3.tbd
+ SystemConfiguration.framework
+ CoreTelephony.framework
+ AdSupport.framework
+ iAd.framework

> [Appsflyer官网指引](https://support.appsflyer.com/hc/en-us/articles/207033486-How-Do-I-Get-Started-)


