## 4.4.13.13 Toy功能扩展

###1. 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.UToy |Toy扩展功能|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.UToy（GameObject）上，开发者不要主动销毁该对象！</font>

###2.快速入门
1. 代码示例      

```cs
void Start() {
 IMSDKApi.UToy.Initialize();
}

IMSDKApi.UToy.ShowBanner(1, this.OnShowBannerCallback);
IMSDKApi.UToy.ShowEndingBanner(this.OnShowEndingBannerCallback);
IMSDKApi.UToy.ShowTermsOfAgree(this.OnShowTermsOfAgreeCallback);
IMSDKApi.UToy.ShowNotice(this.OnShowNoticeCallback);
IMSDKApi.UToy.ShowSettlementFund("zuan1000", "jinbi40000", this.OnShowSettlementFundCallback);

/*
*Show Plate & ShowHelpCenter & ShowCustomerService
*/
IMParamsa paramsa = new IMParamsa();
paramsa["GameID"] = "5";
paramsa["ChracterName"] = "name";
paramsa.questionInfos.Add("GameVersion");
paramsa.questionInfos.Add("CHRACTERID");
IMSDKApi.UToy.ShowPlate(0, paramsa, this.OnShowPlateActionPerformedCallback);
IMSDKApi.UToy.ShowHelpCenter(paramsa);
IMSDKApi.UToy.ShowCustomerService(paramsa);

/*
*获取关系链
*/
IMSDKApi.UToy.GetFriends(0, 1, "invites", this.OnGetFriendsCallback);
IMSDKApi.UToy.ShowFAQ();
IMSDKApi.UToy.ShowForumWithId(1);
IMSDKApi.UToy.SetLocal("zh_CN");//ko_KR en_US ja_JP zh_TW zh_CN de_DE pt_PT pt_BR es_ES ru_RU
IMSDKApi.UToy.SetCountry("CN");//US CN CA JP KR TW DE IT RU BR FR ES

/*
*游客账号备份及迁移
*/
IMSDKApi.UToy.ShowDataBackup();
IMSDKApi.UToy.ShowDataRestore();

```

###3. 模块使用说明
与iMSDKToy登录模块、iMSDKToy分享模块、iMSDKToy关系链模块、iMSDKToy推送模块配合使用

####3.1 基本功能

主要 获取地理信息、获取好友(可邀请)列表、展示协议、展示公告、展示Banner、游客账号数据迁移等辅助功能。

###4. 工程配置说明

####4.1 Android工程配置说明

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

####4.2 iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。

###5. 参考
####5.1关闭Notice结构体及回调代理函数
* 关闭Notice结构体 <font color=blue>IMToyNoticeCloseResult</font>

| 变量 | 说明 |
|  :-- |  :-- |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public string screenName | 当前场景名称 |

* 关闭Notice回调代理函数 <font color=blue>ShowNoticeCallback</font>

| 类型 | 说明 |
|  :--  |  :--  |
| public delegate void ShowNoticeCallback(IMToyNoticeCloseResult result) | 获取展示Notice回调函数，返回关闭Notice结构体 |

####5.2展示Banner结构体及回调代理函数
* 展示Banner结构体 <font color=blue>IMToyBannerResult</font>

| 变量 | 说明 |
|  :--  |  :--  |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public string state | 展示Notice事件状态, 1001:展示notice失败 1002：关闭notice 1003:点击Notice 1004:退出Notice|

* 展示Banner回调代理函数 <font color=blue>ShowBannerCallback</font>

| 类型 | 说明 |
|  :--  |  :--  |
| public delegate void ShowBannerCallback(IMToyBannerResult result) | 展示Banner回调函数，返回浏览器状态结构体 |

####5.3 IMToyUserInfo:Toy玩家信息结构体
| 变量 | 说明 |
|  :--  |  :--  |
| public string memType | User authentication type |
| public string npsn | User identification value in NPA |
| public string subID | Identification value used in the relevant authentication method |
| public string pictureUrl | Profile image |
| public string name | Nickname |
| public string memID | |
| public string age_range_max | |
| public string age_range_min | |
| public string email | |
| public string gender | |
| public string birthDay | |
| public string firstName | |
| public string middleName | |
| public string lastName | |

####5.4 IMToyFriend:Toy关系链信息结构体及回调代理函数
| 变量 | 说明 |
|  :--  |  :--  |
| public int hasNext | 下一页 |
| public IMToyUserInfo friends | 登录账号中已玩该游戏的好友 |
| public IMToyUserInfo invites | 登录账号中未玩该游戏的好友 |

* 获取关系链回调代理函数 <font color=blue>GetFriendsCallback</font>

| 类型 | 说明 |
|  :--  |  :--  |
| public delegate void GetFriendsCallback(IMToyFriend result) | 获取关系链回调函数，返回关系链结构体 |


* UToy方法类 <font color=blue>IMUToy</font>

| 函数名 | 函数说明 |
|  :--  |  :--  |
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数 |
| public void ShowBanner(int groupCode, ShowBannerCallback callback = null) | 展示Banner |
| public void ShowEndingBanner(ShowEndingBannerCallback callback = null) | 展示应用退出时的Banner |
| public void ShowTermsOfAgree(ShowTermsOfAgreeCallback callback = null) | 展示用户协议 |
| public void ShowNotice(ShowNoticeCallback callback = null) | 展示公告 |
| public void ShowSettlementFund(string itemName, string itemPrice, ShowSettlementFundCallback callback = null) | 展示资金支付法规 |
| public void ShowPlate(int group, IMParamsa param, ShowPlateActionPerformedCallback callback = null) | 展示Plate |
|public void GetFriends(int snsType, int nextPage, string filterType, GetFriendsCallback callback = null) | 获取关系链 |
| public void ShowFAQ() | 展示FAQ |
| public void ShowForumWithId(int forumId) | 展示论坛 |
| public String GetLocal() | 获取当前地理位置 |
| public void SetLocal(String local) | 设置当前地理位置 |
| public String GetCountry() | 获取当前所处国家 |
| public void SetCountry(String country) | 设置当前所处国家 |
| public void ShowDataBackup(string title = "", ShowDataBackupCallback callback = null) | 游客账号数据备份 |
| public void ShowDataRestore(string title = "", ShowDataRestoreCallback callback = null) | 游客账号数据迁移 |








