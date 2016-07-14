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

