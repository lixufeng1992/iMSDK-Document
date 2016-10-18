## 6.8.4 iOS 工程配置


###常规配置

+ 工程target->Build Settings > Linking > Other Linker Flags，添加"-all_load" 
+ 工程target->Info->URL Types，添加kakao url scheme, 值为**KAKAO_APP_KEY**，如kakaoxxxxxxxxxx
+ 工程配置info.plist文件中添加配置项KAKAO_APP_KEY

###iOS9适配配置
+ HTTPS适配，在工程配置info.plist添加如下配置项
	```
	<key>NSAppTransportSecurity</key>
<dict>
    <key>NSExceptionDomains</key>
    <dict>
        <key>kakao.com</key>
        <dict>
            <key>NSIncludesSubdomains</key>
            <true/>
            <key>NSExceptionRequiresForwardSecrecy</key>
            <false/>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
        </dict>
        <key>kakao.co.kr</key>
        <dict>
            <key>NSIncludesSubdomains</key>
            <true/>
            <key>NSExceptionRequiresForwardSecrecy</key>
            <false/>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
        </dict>
        <key>kakaocdn.net</key>
        <dict>
            <key>NSIncludesSubdomains</key>
            <true/>
            <key>NSExceptionRequiresForwardSecrecy</key>
            <false/>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
        </dict>
    </dict>
</dict>
	```
	
+ APP跳转白名单,在工程配置info.plist添加如下配置项
	```
	<key>LSApplicationQueriesSchemes</key>
<array>
    <string>kakao{app_key}</string>
    <string>kakaokompassauth</string>
    <string>storykompassauth</string>
    <string>kakaolink</string>
    <string>kakaotalk-4.5.0</string>
    <string>kakaostory-2.9.0</string>
</array>
	```
	其中kakao{app_key}必须改为APP在kakao平台申请的appkey
	
	
	###参考链接
	[官网配置](https://gamecenter.kakao.com/docs/documents/281)
	


