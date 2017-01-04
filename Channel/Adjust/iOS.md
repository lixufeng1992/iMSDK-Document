# Adjust(iOS)配置说明

##IMSDK配置
配置文件**IMSDKAppSetting.bundle/Contents/Resources/app.plist**添加配置项`Adjust`

```
<key>Adjust</key>
	<dict>
		<key>appid</key>
		<string>{yourAppToken}(7d1xuapdriww)</string>
		<key>isDebugMode</key>
		<true(true or false)/>
	</dict>
```

##添加系统库依赖

+ libz.tbd
+ libsqlite3.tbd
+ SystemConfiguration.framework
+ CoreTelephony.framework
+ AdSupport.framework
+ iAd.framework

> [Adjust说明文档](https://github.com/adjust/ios_sdk#sdk-integrate)
> [Adjust currencry code](https://docs.adjust.com/en/event-tracking/supported-currencies/)


