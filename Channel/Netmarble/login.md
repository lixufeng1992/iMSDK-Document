，## Netmarble 登录功能说明

### 登录支持接口列表

|序号|方法名|方法说明|是否支持|备注|
|:-- |:-- |:--|:--|:--|
|1|public bool Initialize()|初始化方法|√| -|
| 2 | public bool Initialize(string channel) | 初始化，并制定登录渠道 |√ | |
| 3 | public bool SetChannel(string channel) | 设置登录渠道| √ | |
| 4 | public string GetChannel() | 获取当前设定渠道 | √ | |
| 5 | public void SetType(string type) | 复杂渠道设置登录类型 | × | |
| 6 | public void Login( <br>&emsp;&emsp;LoginCallback callback = null,<br> &emsp;&emsp;List< string > permissionList = null,<br>&emsp;&emsp;bool needGuid = true) | 一般登录 | √ | |
| 7 | public void StrictLogin( <br>&emsp;&emsp;LoginCallback callback = null,<br> &emsp;&emsp;List< string > permissionList = null,<br>&emsp;&emsp;bool needGuid = true) | 严格登录 | √ | |
| 8 | public void QuickLogin(LoginCallback callback = null) | 快速登录 | × | |
| 9 | public bool IsLogin() | 判断用户是否已经登录 | √ | |
| 10 | public void AutoLogin(LoginCallback callback = null) | 自动登录 | × | |
| 11 | public IMLoginResult GetLoginResult() | 获取当前登录返回数据 | √ | |
| 12 | public void Logout() | 登出当前渠道 | × | |
| 13 | public void Bind(string channel, LoginCallback callback = null) | 绑定到其他渠道账号 | × | |
| 14 | public void GetBindInfo(BindInfoCallback callback= null) | 获取用户绑定渠道资料 | x | |
| 15 | public void SetPlayingReportChannel(string channel) | 设定状态上报渠道 | × | |
| 16 | public void ActivatePlayingReport(string extraJson="") | 上报状态 | × | |
| 17 | public void DeactivatePlayingReport() | 关闭状态上报 | × | |
| 18 | public bool IsChannelAppInstalled() | 是否安装渠道应用 | × | |
| 19 | public bool IsChannelSupportApi() | 应用API版本是否可用 | × | - |



### 登录结果ExtraJson说明
```
{
"region":"GLOBAL",
"iStatus":1,
"joinedCountryCode":"CN",
"playerID":"A98F4F0E430E42FA9685A902F8DA713A",
"channelStatus":0,
"IPAddress":"103.7.29.9",
"countryCode":"CN",
"gameToken":"0AB00145F4C1B1EADDD7D7563AF61FDE020EC75770AC6CC5BD827D0A03D7E04F8E16F083EBA9007F40669489CEF53C8E3C25E8618A295EC3444CE776D3F34A149C6740C46A64E896670BE7808C6A9FDA4525EF43A82FC74BBDBE624BE761A3981EBD426C7E410254AF31F9B50BA426289746FFCF7DAE5D3D813848DB474BC642954AE694A681081B1C55B46D9DE940402ECAB00079E68A91BC3DCF87468159C8A52C455AE524A2C2375B49D2044451B290FDE41220611FF76944F80B4CDEF36DFF14D6413C857AD1B904B9878A39A977AF6E10E247"
}
```
其中，需要重点注意的字段：

iStatus ：用户注销状态
* 1 : 正常状态
* 2 : 待注销状态
* 3 : 已注销状态

channelStatus
自动登录绑定渠道结果
* 0 : 未绑定
* 1 : 绑定，且登录成功
* 2 : 绑定，但登录失败


