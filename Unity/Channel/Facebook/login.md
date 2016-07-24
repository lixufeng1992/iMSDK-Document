## 4.5.1.1 Facebook 登录功能说明

### 登录支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(string channel) | 初始化，并制定登录渠道 |√ | |
| 3 | public bool SetChannel(string channel) | 设置登录渠道| √ | |
| 4 | public string GetChannel() | 获取当前设定渠道 | √ | |
| 5 | public void SetType(string type) | 复杂渠道设置登录类型 | × | |
| 6 | public void Login( <br>&emsp;&emsp;LoginCallback callback = null,<br> &emsp;&emsp;List< string > permissionList = null,<br>&emsp;&emsp;bool needGuid = true) | 一般登录 | √ | |
| 7 | public void StrictLogin( <br>&emsp;&emsp;LoginCallback callback = null,<br> &emsp;&emsp;List< string > permissionList = null,<br>&emsp;&emsp;bool needGuid = true) | 严格登录 | √ | |
| 8 | public void QuickLogin(LoginCallback callback = null) | 快速登录 | √ | |
| 9 | public bool IsLogin() | 判断用户是否已经登录 | √ | |
| 10 | public void AutoLogin(LoginCallback callback = null) | 自动登录 | √ | |
| 11 | public IMLoginResult GetLoginResult() | 获取当前登录返回数据 | √ | |
| 12 | public void Logout() | 登出当前渠道 | √ | |
| 13 | public void Bind(string channel, LoginCallback callback = null) | 绑定到其他渠道账号 | √ | |
| 14 | public void GetBindInfo(BindInfoCallback callback=null) | 获取用户绑定渠道资料 | √ | |
| 15 | public void SetPlayingReportChannel(string channel) | 设定状态上报渠道 | × | |
| 16 | public void ActivatePlayingReport(string extraJson="") | 上报状态 | × | |
| 17 | public void DeactivatePlayingReport() | 关闭状态上报 | × | |
| 18 | public bool IsChannelAppInstalled() | 是否安装渠道应用 | × | |
| 19 | public bool IsChannelSupportApi() | 应用API版本是否可用 | × | - |

### 登录权限说明

  * 权限列表可参考Facebook权限说明：[https://developers.facebook.com/docs/facebook-login/permissions/v2.4](https://developers.facebook.com/docs/facebook-login/permissions/v2.4)
  
  * Facebook 权限分为 读（read）和 写（write）两种模式的权限类型，并且两种权限类型不能在一次登录时同时获取

    >按照Facebook的规则，开发者需要在必要时，获取用户的权限，需要避免一次性获取过多权限，一旦获取权限后，除非用户在配置页面删除该权限，这时候才需要重新获取权限。
    >
    >例如，需要获取用户邮件地址（email）和用户发帖权限（publish_actions），则需要分两次登录 ！

  * 常见权限
    * user_friends 获取用户好友列表，如果需要使用好友排行功能，需要在登录时获取
    * publish_actions 不弹出Facebook界面的分享权限