# Beacon(iOS)配置说明

##IMSDK配置
配置文件**IMSDKAppSetting.bundle/Contents/Resources/app.plist**添加配置项`Appsflyer`

```
<key>Beacon</key>
	<dict>
		<key>channelId</key>
		<string>10010</string>
		<key>appid</key>
		<string>YOUR_APP_ID</string>
	</dict>
```

channelId上架渠道ID，iOS默认为App Store，可以忽略。

##添加系统库依赖

+ SystemConfiguration.framework
+ libz.tbd
+ libstdc++.tbd
+ libsqlite3.tbd
+ CoreTelephony.framework

> [Beacon官网指引](http://beacon.qq.com/help/index.htm)


