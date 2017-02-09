# Netmarble iOS 工程配置

##Netmarble 配置文件 NMConfiguration.plist 设置
+ gameCode ：游戏APPID，必须设置为 Netmarble 分配的值
+ zone：设置平台环境
+ useLog : 设置调试 Log 显示与否, 服务环境里一定要设置为 false
+ useFixedPlayerID：访客模式里即使重新安装 APP，也能够维持 PlayerID 所需的设置。没有设置这个值的话，访客模式重新安装 APP 的话，PlayerID 会变更。
+ OTPLength： 未使用 OTP 功能，忽略
+ OTPLifeCycle： 未使用 OTP 功能，忽略
+ OTPHistoryPeriod： 未使用 OTP 功能，忽略

##添加系统库依赖

+ ibsqlite3.tbd
+ SystemConfiguration.frame
+ libz.tbd
+ AdSupport.framework
+ Security.framework

## xcode 工程设置

1. [Project] > [BuildSettings] > [Other Linker Flags]里添加 -ObjC, -all_load
2. 添加 URLSCHEME , 值为**nm{gameCode}**（{gameCode}部分更改为 Netmarble 发放的值）
3. 添加访问相机、相册所需的用户说明(对应 iOS 10)
4. 添加 ATS 设置允许 APP 的 HTTP 通信

	```
	<key>NSAppTransportSecurity</key>
	 <dict> 
	 	<key>NSAllowsArbitraryLoads</key> <true/>	</dict>
	```

5. 添加 Scheme 白名单

	```
	<key>LSApplicationQueriesSchemes</key> 
	<array>
	// NMGSDKKakao2Kit.framework 使用时添加
		 <string>kakao{app_key}</string> 
		 <string>kakaokompassauth</string> 
		 <string>storykompassauth</string>
		 <string>kakaolink</string> 
		 <string>kakaotalk-4.5.0</string> 
		 <string>kakaostory-2.9.0</string> 
	</array>
```

6. 关闭 Bitcode，Build Settings -> Enable Bitcode:NO 设置后改为 Disable。
7. KeychainItemWrapper Compiler Flags 设置。target -> Build Phases -> KeychainItemWrapper.m 里输入 Compiler Flags **`-fno-objc-arc`** Unity 游戏 ARC(Automatic Reference Counting)默认为 NO，不需要设置 Compiler Flags。
8. 开启 Keychain Sharing, 添加Keychain Groups： **com.netmarble.common**

