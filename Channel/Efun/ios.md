##6.6.3 Efun iOS工程配置
###1. 配置
####1.1 Xcode工程配置
Xcode->Project->Edit Project Settings，打开你的工程配置,在工程配置中找到Linking部分，修改 Other Linker Flags 添加以下参数： -lsqlite3.0 –ObjC


####1.2 SDK所依赖Framework的添加
请在你的工程中添加以下Framework,其中方框外红色的Framework需设置为Optional:(如果不进行设置有可能会造成低版本的ios无法进入游戏)

<font color = red >AdSupport.framework, Social.framework</font>

CFNetwork.framework, CoreMedia.framework, EventKitUI.framework, iAd.framework, FacebookSDK.framework

StroeKit.framework, QuartzCore.framework, SystemConfiguration.framework, CoreTelephony.framework, 

Accounts.framework, Security.framework, CoreMotion.framework, MediaPlayer.framework, EventKit.framework

CoreLocation.framework, MessageUI.framework, MobileCoreServices.framework, libz.dylib(Xcode7.3或以上为libz.tbd), AudioToolbox.framework,

AVFoundation.framework, CoreData.framework ,CoreText.framework
####1.3 工程中Info.plist文件相关选项配置(要完全按配置，否则会crash)
+ 游戏的BundleID为：com.vqw.hkqmcs

+ 添加 URLSchemes、URL identifier 与 FacebookAppID、FacebookDisplayName 和程序标识符

	+ FacebookAppID : 1183480865030141   
	+ FacebookDisplayName : 全民超神-HK    
	+ URL Schemes : fb1183480865030141 和 hkqmcsios和 com.vqw.hkqmcs   
	+ URL identifier : com.vqw.hkqmcs

+ 若使用Xcode7或以上打包的话，请继续加入以下部分：  

  + NSAppTransportSecurity 的子项 NSAllowsArbitraryLoads 设为：YES

  + LSApplicationQueriesSchemes 设上 Facebook的urlSchemes白名单   
  
  ```
  
  <key>LSApplicationQueriesSchemes</key>   
	<array>   
		<string>fbapi</string>   
		<string>fbapi20130214</string>
		<string>fbapi20130410</string>
		<string>fbapi20130702</string>
		<string>fbapi20131010</string>
		<string>fbapi20131219</string>
		<string>fbapi20140410</string>
		<string>fbapi20140116</string>
		<string>fbapi20150313</string>
		<string>fbapi20150629</string>
		<string>fbauth</string>
		<string>fbauth2</string>
		<string>fb-messenger-api20140430</string>
	</array>

	```



##1.4 添加KeyChainGroup描述
在Build Setting中指定设置项Code Signing Entilements的值为SDK中配置文件EfunConfig/EFUNSDK_iOS.entilements，如果游戏本身也有使用Keychain，则只需将该配置文件中KeyChainGroup描述添加到游戏工程原本的.entilements文件中即可。

PS：由于Capabilities下的KeyChain Sharing开关是与开发者账号中的应用配置相关的，无需理会，只要用我们给到的证书打包即可  

##1.5 IMSDKAppsettings.bundle


```
  
  </dict>
	<key>Efun</key>
	<dict>
		<key>gamecode</key>
		<string>hkqmcsios</string>
	</dict>

```

