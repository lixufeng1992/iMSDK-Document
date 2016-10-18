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
	
	
	###错误码
	####HTTP请求
| Code	| 状态 |
| :-- | :-- |
| 200 | API 调用成功。Response Body会根据各个API 有区别 |
| 400 | 错误的请求。主要与API需要的必要参数相关 |
| 401 |	验证错误。主要与Unauthorized, Invalid Token 等用户的token相关 |
| 403 |	权限/鉴权等错误 |
| 500 |	内部服务器错误 |
| 503 | 维护中 |

	####通用错误码
| Code | Enum | 状态 |	Http status code |
| :-- | :-- | :-- | :-- |
| -1 | KOServerErrorUnknown | 服务器处理过程中发生错误 (internal error)	| 400 |
| -2 | KOServerErrorBadParameter | 未包含必要参数，调用的参数不是对应的数据类型或超出许可范围的情况。| 400 |
| -4 | KOServerErrorBlocked | 制裁账号或特定服务中，因制裁该用户的制裁，禁止调用API的情况	 | 400 |
| -5 | KOServerErrorSecurity	| App中不存在该API相关的权限时 | 403 |
| -10 | KOServerErrorApiLimitExceed | 超出允许的请求次数时，message quota等	| 400 |
| -301 |	KOServerErrorNoSuchApp	| 未注册的APPkey的请求或不存在的APP的请求。	| 400 |
| -401 | KOServerErrorInvalidAccessToken |Appkey/token 错误时。例如，不存在appkey（重新生成后，不使用的历史appkey的情况）或与 agent信息不一直的appkey类型的情况。 (后续处理: 确认appkey的值和类型。用refresh token更新token后重试) | 401 |
| -9798	| 无 |维护中	| 503|

	####登录错误码
	
| Code	| Enum	| 状态	| Http status code |
| :-- | :-- | :-- | :-- |
| -101	| KOServerErrorNotSignedUpUser |	只对绑定用户许可的API中，当未绑定用户请求时.	| 400 |  
| -102 |  KOServerErrorAlreadySignedUpUser | 只对未绑定用户许可的API中，当绑定用户请求时.	| 400 |
| -103	| 对于调用不存在的kakao账号 |	400	|
| -402	| KOServerErrorInsufficientScope	对于访问该 API的资源，未得到用户同意时。	|  403  |

	####维护用户信息与其他
| Code	| Enum	 | 状态	| Http status code |
| :-- | :-- | :-- | :-- |
| -201 | KOServerErrorInvalidUserPropertyKey | 调用管理API时，参数结构不合理时	| 400 |
| -501 | KOServerErrorNotTalkUser |只给注册kakao账号的用户授权的API中，当未注册kakao账号的用户发起请求时 (例. kakaotalk API).	| 400 |



