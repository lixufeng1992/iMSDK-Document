### iOS 配置

* iMSDK配置

 添加iOS插件后，在XCode工程中找到**IMSDKAppSetting.bundle/Contents/Resources/app.plist**文件，增加或修改如下配置：

 ```plist
 <key>Garena</key>
 <dict>
     <key>isDebugMode</key>
     <true/>
     <key>loginKey</key>
     <string>49c1b7af60b1f5557005d101f1f8aa6e0a185c286ee630612ecc2c54c7ac7b27</string>
 </dict>
 ```
 
 - isDebugMode，标识是否启用Garena的Debug模式，正式环境应该设置为`false`。
 - loginKey，由Garena侧分配，正式环境和测试环境不同。

* 工程Plist文件配置

 找到或新建如下节点:

 ```plist
 <key>CFBundleURLTypes</key>
 <array>
     <dict>
		 <key>CFBundleTypeRole</key>
		 <string>Editor</string>
		 <key>CFBundleURLName</key>
		 <string>facebook</string>
		 <key>CFBundleURLSchemes</key>
		 <array>
			 <string>fb423362744481374</string>
		 </array>
	 </dict>
	 <dict>
		 <key>CFBundleTypeRole</key>
		 <string>Editor</string>
		 <key>CFBundleURLName</key>
		 <string>gop</string>
		 <key>CFBundleURLSchemes</key>
		 <array>
			 <string>gop100050</string>
		 </array>
	 </dict>
 </array>
 <key>FacebookAppID</key>
 <string>423362744481374</string>
 <key>GOPAppID</key>
 <string>100050</string>
 <key>LSApplicationQueriesSchemes</key>
 <array>
	 <string>beetalk</string>
	  <string>garenagc</string>
	 <string>fb</string>
	 <string>fbapi</string>
	 <string>fbapi20130214</string>
	 <string>fbapi20130410</string>
	 <string>fbapi20140410</string>
	 <string>fbapi20140116</string>
	 <string>fbapi20150313</string>
	 <string>fbapi20150629</string>
	 <string>fbauth</string>
	 <string>fbauth2</string>
	 <string>fb-messenger-api20140430</string>
     <string>gop100050</string>
 </array>
 <key>NSAppTransportSecurity</key>
 <dict>
     <key>NSAllowsArbitraryLoads</key>
     <true/>
 </dict>
 ```

   - FacebookAppID，Garena侧提供的`Facebook App ID`。
   - GOPAppID，Garena侧提供的`Garena App ID`。