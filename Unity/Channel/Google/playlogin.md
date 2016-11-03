## Google Play登录模块

### 支持接口列表

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

一般采用默认的登录权限即可，如果有特殊需求，请联系iMSDK

### 工程配置

#### Android工程配置

* 完成[通用配置](../../../Channel/Google/android.md)
  
  配置网络权限和GMS版本配置
  
* 添加配置

  ```xml
  <meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ 263738040849" />
  <meta-data android:name="com.google.android.gms.serverclientid"
    android:value="263738040849-kgcholbfoi8163lpn8ke3l3dsc3pvtu4.apps.googleusercontent.com" />
  ```
  
  注意：value需要修改为游戏对应的值