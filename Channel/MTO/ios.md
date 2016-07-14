## MTO iOS 工程配置    
###[MTO Facebook配置](Channel/Facebook/ios.md)

Facebook所需要的配置在官方文档都有详细说明，请参考：[https://developers.facebook.com/docs/ios/getting-started/](https://developers.facebook.com/docs/ios/getting-started/)

* iMSDK资源文件Plist文件配

  添加完iMSDK的iOS插件后，在XCode工程中找到IMSDKAppSetting.bundle/Contents/Resources/app.plist文件，增加或修改如下配置：
  
  ```xml
  <key>Facebook</key>
  <dict>
      <key>appid</key>
      <string>423362744481374</string>
      <key>displayname</key>
      <string>IMSDKSample</string>
  </dict>
  ```
  
  其中，appid和displayname的string值需要修改成游戏的真实值

* 工程Plsit文件配置

  ```xml
  <key>CFBundleURLTypes</key>
  <array>
    <dict>
      <key>CFBundleURLSchemes</key>
      <array>
        <string>fb{your-app-id}</string>
      </array>
    </dict>
  </array>
  <key>FacebookAppID</key>
  <string>{your-app-id}</string>
  <key>FacebookDisplayName</key>
  <string>{your-app-name}</string>
  ```
  
  其中，{your-app-id}需要替换成游戏的App ID，另外需要说明的是：FacebookDisplayName需要与Facebook上注册名保持一致，并且需要与编译时的Product Name一致
  
* iOS 9 Plist配置，因为苹果在这一版本修改了安全规则，如果需要支持iOS9，需要添加如下配置
 
 ```xml
  <key>NSAppTransportSecurity</key>
  <dict>
    <key>NSExceptionDomains</key>
    <dict>
      <key>facebook.com</key>
      <dict>
        <key>NSIncludesSubdomains</key> <true/>        
        <key>NSThirdPartyExceptionRequiresForwardSecrecy</key> <false/>
      </dict>
      <key>fbcdn.net</key>
      <dict>
        <key>NSIncludesSubdomains</key> <true/>
        <key>NSThirdPartyExceptionRequiresForwardSecrecy</key>  <false/>
      </dict>
      <key>akamaihd.net</key>
      <dict>
        <key>NSIncludesSubdomains</key> <true/>
        <key>NSThirdPartyExceptionRequiresForwardSecrecy</key> <false/>
      </dict>
    </dict>
  </dict>
 ```
 
* Facebook SDK 4.5以上版本iOS 9 Plist配置。如果用新版的Facebook SDK，需要新增如下配置：
  
  ```xml
  <key>NSAppTransportSecurity</key>
  <dict>
    <key>NSExceptionDomains</key>
    <dict>
      <key>facebook.com</key>
      <dict>
        <key>NSIncludesSubdomains</key> <true/>        
        <key>NSThirdPartyExceptionRequiresForwardSecrecy</key> <false/>
      </dict>
      <key>fbcdn.net</key>
      <dict>
        <key>NSIncludesSubdomains</key> <true/>
        <key>NSThirdPartyExceptionRequiresForwardSecrecy</key>  <false/>
      </dict>
      <key>akamaihd.net</key>
      <dict>
        <key>NSIncludesSubdomains</key> <true/>
        <key>NSThirdPartyExceptionRequiresForwardSecrecy</key> <false/>
      </dict>
    </dict>
  </dict>
  ```
  
  如果Facebook SDK版本为4.6以上版本，则还需要添加如下配置：
  
  ```xml
  <key>LSApplicationQueriesSchemes</key>
  <array>
    <string>fbapi</string>
    <string>fb-messenger-api</string>
    <string>fbauth2</string>
    <string>fbshareextension</string>
  </array>
  ```