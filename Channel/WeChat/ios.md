### 6.3.3 iOS 配置

* iMSDK配置修改

 添加完iOS插件后，在XCode工程中找到**IMSDKAppSetting.bundle/Contents/Resources/app.plist**文件，增加或修改如下配置：

 ```plsit
 <key>WeChat</key>
 <dict>
 <key>appid</key>
 <string>wxef53dd2d66ca6c54</string>
 </dict>
 ```

 其中，appid值wxef53dd2d66ca6c54需要修改为游戏自己微信的App ID

* 工程Plist文件配置

 找到或新建如下节点:

 ```plist
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