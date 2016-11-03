# Bugly(iOS)配置说明

##IMSDK配置
配置文件**IMSDKAppSetting.bundle/Contents/Resources/app.plist**添加配置项`Bugly`

```
<key>Bugly</key>
	<dict>
		<key>unexpectedTerminatingDetection</key>
		<true/>
		<key>appid</key>
		<string>YOUR_APP_ID</string>
	</dict>
```

unexpectedTerminatingDetection配置项，设置是否开启非正常闪退异常捕获。适用于1.1.2及以上版本的IMSDKStatBugly.framework

##添加系统库依赖

+ CFNetwork.framewor
+ SystemConfiguration.framework
+ JavaScriptCore.framework
+ Security.framework
+ libstdc++.tbd

> [Bugly官网指引](https://bugly.qq.com/docs/user-guide/instruction-manual-ios/?v=20161012083243)




