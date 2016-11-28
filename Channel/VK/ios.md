##VK iOS工程配置

###1、添加 URL schems
+ 如果要通过VK app进行授权的话需要进行URL Scheme设置 vk+APP_ID (e.g. vk1234567).

###2、 iOS 9配置

+ 设置nohttps  

```

<key>NSAppTransportSecurity</key>
<dict>
    <key>NSExceptionDomains</key>
    <dict>
        <key>vk.com</key>
        <dict>
            <key>NSExceptionRequiresForwardSecrecy</key>
            <false/>
            <key>NSIncludesSubdomains</key>
            <true/>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
        </dict>
    </dict>
</dict>
```

+ 添加白名单

```

<key>LSApplicationQueriesSchemes</key>
<array>
    <string>vk</string>
    <string>vk-share</string>
    <string>vkauthorize</string>
</array>
```  


