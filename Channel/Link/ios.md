### iOS 配置

* iMSDK配置

 添加iOS插件后，在XCode工程中找到**IMSDKAppSetting.bundle/Contents/Resources/app.plist**文件，增加或修改如下配置：

 ```plist
 <key>Link</key>
 <dict>
     <key>isDebugMode</key>
     <true/>
     <key>twitterConsumerKey</key>
     <string>HZ7K6ONuzsOsA2NV625Uokjmw</string>
     <key>twitterConsumerSecret</key>
     <string>GYKCYX0YDeD4bAZ7tfzEqAy5paawhRPtmUfSMP29GQbx6RXQit</string>
     <key>googleClientID</key>
     <string>909898481297-jtu91mphbjarka77ama4sjqgk3umgqag.apps.googleusercontent.com</string>
     <key>linkBaseUrl</key>
     <string>https://prd-link.sorakuro.com</string>
     <key>linkAccessToken</key>
     <string>a41bbbb9d01de59b984ac098df0a83a6</string>
     <key>keyStoreIdentifier</key>
     <string></string>
 </dict>
 ```
 
 - isDebugMode，标识是否启用Link的Debug模式，正式环境应该设置为`false`。
 - linkAccessToken，由Link侧提供的配置，正式环境和测试环境不同。
 - linkBaseUrl，由Link侧提供的Link配置，正式环境和测试环境配置不同。
 - twitterConsumerKey、twitterConsumerSecret，由Link侧提供的Twitter配置。
 - googleClientID，由Link侧提供的Google Plus配置

* 工程Plist文件配置

 修改或新建如下节点:

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
             <string>fb414489312041120</string>
         </array>
     </dict>
     <dict>
         <key>CFBundleTypeRole</key>
         <string>Editor</string>
         <key>CFBundleURLName</key>
         <string>com.aiming.linkdev</string>
         <key>CFBundleURLSchemes</key>
         <array>
             <string>com.aiming.linkdev</string>
         </array>
     </dict>
 </array>
 <key>FacebookAppID</key>
 <string>414489312041120</string>
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
 <key>AimingLinkDeleteAuthToken</key>
 <true/>
 ```

   - FacebookAppID，由Link侧提供的`Facebook App ID`。
   - AimingLinkDeleteAuthToken，设置应用删除后是否重置LinkAuthToken。
   - Url Scheme，设置Facebook和Link的Url Scheme

