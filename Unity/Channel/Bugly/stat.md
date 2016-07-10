# Bugly 功能说明

## Bugly 登录功能说明

### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | √ | - |
| 3 | public bool SetChannel(string channel) | 设置登录渠道| √ | - |
| 6 | public void reportEvent | 事件上报 | √ | - |
| 7 | public void reportPurchase() | 购买行为上报 | √ | - |
| 8 | public void trackEvent() | 事件跟踪 | √ | - |
| 9 | public bool trackPage() | 判断用户是否已经登录 | √ | - |
| 10 | public void speedTest() | 自动登录 | √ | - |
| 11 | public void reportCrash() | 获取当前登录返回数据 | √ | - | 
| 12 | public void reportAutoExceptionReport() | 登出当前渠道 | √ | - |


### 登录权限说明

  * 权限列表可参考Facebook权限说明：[https://developers.facebook.com/docs/facebook-login/permissions/v2.4](https://developers.facebook.com/docs/facebook-login/permissions/v2.4)
  
  * Facebook 权限分为 读（read）和 写（write）两种模式的权限类型，并且两种权限类型不能在一次登录时同时获取

    >按照Facebook的规则，开发者需要在必要时，获取用户的权限，需要避免一次性获取过多权限，一旦获取权限后，除非用户在配置页面删除该权限，这时候才需要重新获取权限。
    >
    >例如，需要获取用户邮件地址（email）和用户发帖权限（publish_actions），则需要分两次登录 ！

  * 常见权限
    * user_friends 获取用户好友列表，如果需要使用好友排行功能，需要在登录时获取
    * publish_actions 不弹出Facebook界面的分享权限