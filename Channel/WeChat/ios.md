### 6.3.3 iOS 配置

* iMSDK资源文件Plist文件配

 添加完iMSDK的iOS插件后，在XCode工程中找到IMSDKAppSetting.bundle\/Contents\/Resources\/app.plist文件，增加或修改如下配置：

 ```xml
 <key>WeChat</key>
 <dict>
 <key>appid</key>
 <string>wxef53dd2d66ca6c54</string>
 </dict>
 ```

 其中，string值wxef53dd2d66ca6c54需要修改为游戏自己微信的App ID

* 工程Plsit文件配置

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
 ```

 其中，string值wxef53dd2d66ca6c54需要修改为游戏自己微信的App ID