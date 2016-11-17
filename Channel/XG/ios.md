# XG(iOS)配置说明

##IMSDK配置
配置文件**IMSDKAppSetting.bundle/Contents/Resources/app.plist**添加配置项`XG`

```
<key>XG</key>
	<dict>
		<key>appid</key>
		<string>YOUR_APP_ID</string>
		<key>appkey</key>
		<string>YOUR_APP_KEY</string>
	</dict>
```

##添加系统库依赖

+ libz.tbd
+ CFNetwork.framework
+ SystemConfiguration.framework
+ CoreTelephony.framework
+ Security.framework

> [信鸽（iOS）接入指引](http://developer.qq.com/wiki/xg/信鸽基础介绍/信鸽基础介绍.html)


