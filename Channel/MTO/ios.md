## MTO iOS 工程配置    
###1.[MTO Facebook配置参考Facebook配置](../Facebook/ios.md) 
###2.MTO Google plus 配置  
* 添加GoogleService-Info.plist，并根据业务修改相应配置项
* 添加google与bundle ID的URL Scheme   
```xml
         <dict>
			<key>CFBundleTypeRole</key>
			<string>Editor</string>
			<key>CFBundleURLName</key>
			<string>google</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>REVERSED_CLIENT_ID(在GoogleServer-Info.plist中)</string>
			</array>
		</dict>
		<dict>
			<key>CFBundleTypeRole</key>
			<string>Editor</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>Bundle ID</string>
			</array>
		</dict>
```   
###3.Xcode配置   
* 在 Build Settings =》Other linker Flags中添加 -ObjC；
* 在 info中, 做如下修改:   
  * 关闭 Bitcode (Xcode7 only)     
  * 关闭 NSAppTransportSecurity:

  ```
  <key>NSAppTransportSecurity</key> <dict>
  <key>NSAllowsArbitraryLoads</key>
      <true/>
  </dict>
  ```
  * URL Schemes
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
