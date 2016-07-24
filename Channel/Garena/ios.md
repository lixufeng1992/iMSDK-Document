### iOS 配置

* iMSDK配置

 添加iOS插件后，在XCode工程中找到**IMSDKAppSetting.bundle/Contents/Resources/app.plist**文件，增加或修改如下配置：

 ```xml
 <key>Garena</key>
 <dict>
     <key>isDebugMode</key>
     <true/>
     <key>loginKey</key>
     <string>49c1b7af60b1f5557005d101f1f8aa6e0a185c286ee630612ecc2c54c7ac7b27</string>
 </dict>
 ```

 其中，string值wxef53dd2d66ca6c54需要修改为游戏自己微信的App ID

* 工程Plist文件配置

 找到或新建如下节点:

 ```xml
 <key>CFBundleURLTypes</key>
     <array>
     <dict>
         <key>CFBundleURLSchemes</key>
         <array>
             <string>wxef53dd2d66ca6c54</string>
         </array>
     </dict>
 </array>
 <key>LSApplicationQueriesSchemes</key>
 <array>
     <string>wechat</string>
	 <string>weixin</string>
 </array>
 <key>NSAppTransportSecurity</key>
     <dict>
	 <key>NSAllowsArbitraryLoads</key>
     <true/>
 </dict>
 ```

 其中，string值wxef53dd2d66ca6c54需要修改为游戏自己微信的App ID