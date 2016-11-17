# MTA(iOS)配置说明

##IMSDK配置
配置文件**IMSDKAppSetting.bundle/Contents/Resources/app.plist**添加配置项`MTA`

```
<key>MTA</key>
	<dict>
		<key>appid</key>
		<string>ISBC23T54RZ9</string>
	</dict>
```

##添加系统库依赖

+ libz.dylib
+ libsqlite3.dylib
+ SystemConfiguration.framework
+ CoreTelephony.framework
+ AdSupport.framework

> [MTA（iOS）快速接入](http://developer.qq.com/wiki/mta/iOS接入/MTA（iOS）快速接入/MTA（iOS）快速接入.html)


