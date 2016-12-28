##VNG iOS 工程配置   

###1.[VNG Facebook配置参考Facebook配置](../Facebook/ios.md) 

###2.Xcode配置   
* 在 Build Settings =》Other linker Flags中添加 -ObjC；
* 在 info中, 做如下修改:   
  * 关闭 Bitcode (Xcode7 only)     
 
  * LSApplicationQueriesSchemes
  ```
   <key>LSApplicationQueriesSchemes</key>
   <array>
   <string>zalo</string>
   <string>zalosdk</string>
   <string>fbapi</string>
   <string>fb-messenger-api</string>
   <string>fbshareextension</string>
   <string>fbauth2</string>
   </array>
  ```
* BundleId,需要跟VNG确认。(iMSDK 测试为: vn.gs5.cfm)

###3. IMSDKAppSetting.bundle配置
+ app.plist 添加VNG配置信息，具体信息需要跟VNG确认

```
<key>VNG</key>
	<dict>
		<key>gameid</key>
		<string>CFMOBILESEA(渠道若为VNG则为：CFMOBILE；若为VNGSEA则为：CFMOBILESEA)</string>
		<key>actlable</key>
		<string></string>
		<key>appsflyerdevkey</key>
		<string>test</string>
		<key>appleappid</key>
		<string>222</string>
		<key>actconvertionid</key>
		<string></string>
		<key>ggclientid</key>
		<string></string>
		<key>ggserverclientid</key>
		<string></string>
		<key>paymentappid</key>
		<string>44</string>
		<key>gameversion</key>
		<string>v1.1.1</string>
		<key>zaloappid</key>
		<string>1812423796061342251</string>
	</dict>
```
###4.添加系统库

```
AddressBook.framework   
AdSupport.framework   
CoreLocation.framework   
CoreTelephony.framework   
CoreGraphics.framework   
QuartzCore.framework   
StoreKit.framework    
AVFoundation.framework    
MediaPlayer.framework    
AssetsLibrary.framework    
CoreMotion.framework    
Security.framework     
SystemConfiguration.framework    
libz.tbd    
libc++.tbd  
```


