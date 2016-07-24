## iMSDK Server 端常见错误码

| 错误码 | 返回信息 | 错误说明 |
| :-- | :-- | :-- |
| 5 | need google authcode | 需要google提供授权 |
| 4 | the same openid! | 相同的openid无需恢复 |
| 3 | restore this sns account! | 恢复这个社交渠道，请调用restore接口 |
| 2 | connect this sns channel! | 挂载这个社交渠道，请调用reconnect接口 |
| 1 | success | 成功 |
| -1 | failure | 失败 |
| -101 | ChannelHashId query guid is failure! | ChannelHashId2Guid失败 |
| -102 | Guid query ChannelHashId failure | Guid2ChannelHashId失败 |
| -103 | tag Guid table record delete failure | 标识Guid表记录被删除失败 |
| -104 | tag ChannelHashId table record delete failure | 标识ChannelHashId表记录被删除失败 |
| -105 | add Guid table record is failure | 添加Guid表记录失败 |
| -106 | add ChannelHashId table record is failure | 添加ChannelHashId表记录失败 |
| -107 | no params ChannelHashId | 没有ChannelHashId |
| -108 | no params ChannelId | 没有传入ChannelId |
| -109 | no params Guid | 没有传入Guid |
| -110 | Guid is un Avali | guid无效 |
| -111 | Channel is un avail | 渠道无效 |
| -112 | Sex is un avail | 性别无效 |
| -113 | Status is un avail | 状态无效 |
| -114 | UserName is un avail | 用户昵称无效 |
| -115 | Modify user nicename is failure | 修改Guid表记录用户昵称失败 |
| -116 | Modify user Sex is failure | 修改Guid表记录用户性别失败 |
| -117 | Modify user Age is failure | 修改Guid表记录用户年龄失败 |
| -118 | Modify user Ip is failure | 修改Guid表记录IP失败 |
| -119 | modify Guid table record is failure | 修改Guid表记录失败 |
| -120 | modify ChannelHashId table record is failure | 修改ChannelHashId表记录失败 |
| -121 | add user record is failure | 添加用户失败 |
| -122 | ChannelId no play this game | ChannelHashId暂时没有玩过这个游戏 |
| -123 | ChannelIds Openid error | ChannelHashId查到的Openid与传参不匹配 |
| -124 | openid input is eaqual to db or src, no need to change | ChannelHashId查到的Openid与传参一致，无需修改 |
| -125 | update guid userInfo failure | 更新iguid表时失败 |
| -126 | not a short gameId game | 非32位短帐号游戏 |
| -127 | old openid empty | 在oldOpenid表中没有对应记录 |
| -128 | delete openid failure  | 删除openid失败 |
| -129 | add openid failure  | 添加openid到db失败 |
| -130 | delete Guid failure  | 删除openid失败 |
| -131 | update Openid failure  | 删除openid失败 |
| -132 | guid is disable status! | GUID为停用状态 |
| -133 | guid is delete status! | GUID为删除状态 |
| -134 | openid is disable status! | Openid为停用状态 |
| -135 | openid is delete status! | Openid为删除状态 |
| -136 | no openid input params! | 没有传入openid参数 |
| -201 | verify failure! | facebook鉴权失败 |
| -202 | user account is not available! | 用户状态为停用 |
| -203 | user account was deleted! | 用户状态为删除态 |
| -204 | user session is failure! | 用户登录态过期 |
| -205 | user session is error! | 错误的用户登录态 |
| -206 | user session operation is failure | 保存用户登录态到memcache失败 |
| -207 | get user session is failure! | 获取用户登录态到memcache失败 |
| -208 | del user session is failure! | 删除用户登录态到memcache失败 |
| -209 | no appid params or no appsecret params! | 没有传入APPID或者不存在appid对应；的appsecret |
| -210 | facebook verify failure! | facebook鉴权失败 |
| -211 | WEIXIN verify failure! | WEIXIN鉴权失败 |
| -212 | apple verify failure! | apple鉴权失败 |
| -213 | google verify failure! | google鉴权失败 |
| -214 | guest mod set failure! | 使用游客模式失败 |
| -215 | verify params is error! | 鉴权传递参数错误 |
| -216 | facebook request interface unset | facebook请求接口不存在 |
| -217 | facebook request is failure | facebooke请求失败 |
| -218 | guest login failure! | 启用游客模式失败 |
| -219 | Invalid request! | 请求无效 |
| -220 | Invalid param gameid | businessid不是有效的参数 |
| -221 | add openid to channelId failure | 添加用户Guid到游戏关系失败 |
| -222 | add channelid to openid failure | 添加CHANNELID到游戏关系失败 |
| -223 | need authorize openid play this game | guid有到此游戏的权限， 但是openid之前没有玩过此游戏； |
| -224 | add user to gameid failure! | 添加用户到玩过此游戏的对应关系失败 |
| -225 | channel param is error! | 平台参数错误或无效 |
| -226 | params is error! | 参数错误 |
| -227 | params gameid is error! | 传参gameid错误 |
| -228 | update openid failure  | 更新用户Openid失败 |
| -229 | check login failure  | isLogin返回失败 |
| -230 | get weixin UserInfo failure! | 通过accesstoken和openid去获取用户信息失败 |
| -231 | RET_USERVERIFY_SESSION_ERROR | 用户第3方鉴权信息kv操作失败 |
| -233 | update token info failure! | 更新token信息失败 |
| -234 | weixin req access_tokens expire_in is failure! | 微信返回token有效期失败 |
| -235 | weixin req Openid is failure | 微信返回OPenid失败 |
| -236 | weixin req token is failure | 微信返回token失败 |
| -237 | weixin req refresh_token is failure! | 微信返回refresh_token失败 |
| -238 | facebook token is Invalid | facebook token 过期 |
| -239 | google token is Invalid | google token 过期 |
| -240 | weixin token is Invalid | weixin token 过期 |
| -241 | facebook appid info is error | facebook gameid对应appInfo 配置错误 |
| -242 | google appid info is error | google gameid对应appInfo 配置错误 |
| -243 | weixin appid info is error | weixin gameid对应appInfo 配置错误 |
| -244 | weixin get relationship failure! | weixin 获取好友关系链失败 |
| -245 | get ticket failure! | 获取ticket失败 |
| -246 | request illegal! | 非法请求 |
| -247 | not need update accesstoken! | 更新token失败或不需要更新token信息 |
| -248 | Zalo verify is failure! | Zalo鉴权失败 |
| -249 | Zalo getfriends is failure! | Zalo鉴权失败 |
| -250 | Zalo appinfo get failure! | zalo应用信息拉取失败 |
| -251 | no params openid | 没有传入OPENID |
| -252 | no params guid | 没有传入GUID |
| -253 | no params iChannelHashId | 没有传入iChannelHashId |
| -254 | params iChannelHashId is illegal | iChannelHashId illegal |
| -255 | Zalo verify Guest channel is failure! | Zalo鉴权zalo游客模式失败 |
| -256 | 37wan verify is failure! | 37wan鉴权失败 |
| -257 | get return info failure! | 拿取返回信息失败 |
| -258 | check and login is failure! | 检查并登录 |
| -259 | can not support this channel or channel unset! | 不支持此渠道或渠道无效 |
| -260 | google verify info memcd get failure! | google鉴权信息cache获取失败 |
| -261 | Link verify is failure! | link鉴权失败 |
| -262 | oauth config is error or no info! | 应用配置信息错误或没有配置 |
| -263 | sign cannot use many times! | 37wan不能重复使用ssign |
| -264 | Fb had other user relation, can not bind this user! | App37wan FB存在openid了，不能在进行绑定到别的37Wan上 |
| -265 | zalo token unexpiretime | zalo token 过期, 建议前端重新登录授权 |
| -266 | oas sign cannot use many times! | oas不能重复使用ssign |
| -267 | oasgames verify is failure! | oasgames鉴权失败 |
| -268 | viber verify is failure! | viber鉴权失败 |
| -269 | feiliu verify is failure! | feiliu鉴权失败 |
| -270 | viber get relationship failure! | viber获取好友关系链失败 |
| -271 | garena verify failure | garena 鉴权失败 |
| -272 | vk verify failure | vk verify failure |
| -273 | toy verify failure | toy verify failure |
| -274 | efun verify failure | efun verify failure |
| -275 | kakao verify failure | kakao verify failure |
| -276 | MTO verify failure | kakao verify failure |
| -301 | bind relationship is failure,because openid unset | 绑定失败,有可能的原因是openid被删除或者不存在 |
| -302 | you already bound this channel! | 之前绑定过，不能再进行绑定了 |
| -305 | bind: usersission wrong | session 空 |
| -307 | bind: openid exist, binding forbidden | 已经存在对应openid，不允许绑定 |
| -308 | bind: guid exist, binding forbidden | 已经存在对应guid，不允许绑定 |
| -310 | bind: innertoken error | 用户的内部token错误 |
| -312 | binding the wrong channel | 绑定渠道错误 |
| -313 | params gameid is error! | 传参gameid错误 |
| -314 | params openid is error! | 传参openid错误 |
| -317 | bind: params guid is error! | 传参guid错误 |
| -318 | unbind: params channel is error! | 解绑传参channel错误 |
| -319 | garena_bindurl is test fail! | garena绑定判断失败 |
| -401 | no params sAppChannelId | 没有传入APP对应的CHANNELID或者不存在appid对应；的appsecret |
| -402 | get FriendList is failure! | 获取好友列表失败 |
| -403 | This channel no friend list! | 此平台无好友关系链 |
| -404 | no sAppChannelId to get Friendlist! | 没有app对应的channelid |
| -405 | sns token is failure! | 第3方token失效 |
| -501 | tags params is error! | Tags入参错误 |
| -502 | add tag to tb_openid2tag failure! | tag 插入到openid2tag表失败 |
| -503 | add tag to tb_tag2openid failure! | tag 插入到tag2oepnidb失败 |
| -504 | get tagid list failure! | 获取tagidlist 失败 |
| -505 | query tag is failure! | 查询tag失败 |
| -506 | this openid has no tag | 此玩家的没有tag |
| -507 | no push record! | 此玩家没有tag信息 |
| -508 | push personal taginfo query failure! | 查询此玩家对应tag信息失败 |
| -509 | push query openid by tag and gameid is failure! | 查询tag对应游戏的玩家失败 |
| -510 | push sql to Gameid2tag failure! | 插入到GameId分表失败 |
| -601 | paras email is illegal! | 入参email不合法 |
| -602 | logind innertoken or Openid params is error!, |
| -603 | write personal info is failure! | 写入个人信息失败 |
| -604 | no Personal info! | 没有查询到个人信息 |
| -700 | params sGuestId is error | 传入的登录态和sGuestId不匹配 |
| -701 | can not restore to strong relation account on! | 不能恢复到存在强关联关系的账户 |
| -702 | save confirmcode is fail! | 保存用户确认码到memcache失败 |
| -703 | get confirmcode is fail! | 获取用户确认码到memcache失败 |
| -704 | del confirmcode is fail! | 删除用户确认码到memcache失败 |
| -705 | ConfireCode unavail | 用户确认码失效 |
| -706 | no openid reconnect fail! | 当前openid不存在此渠道，直接挂载此渠道失败 |
| -707 | had openid reconnect fail! | 当前openid存在此渠道，再次挂载此渠道时操作失败 |
| -708 | openid reconnect fail![exception] | 当前openid存在此渠道，异常的失败 |
| -709 | connect or restore model select error! | 模式选择错误，比如强关联模式，选成了弱关联模式处理了 |
| -710 | no openid restore fail! | 当前openid不存在此渠道，snsOpenid也不存在，直接关联此渠道失败 |
| -711 | had openid restore fail! | 当前登录态存在这个渠道的强关联，sns不存在openid时，不用恢复 |
| -712 | openid restore fail![exception] | 当前openid存在此渠道，异常的失败 |
| -713 | platform is Err! | 错误的平台 |
| -714 | is not sns model relation! | 不是强SNS社交模式游戏 |
| -715 | this account can only one migrate! | 平台迁移只能做一次哦；当前登录态返回的，返回失败，原因是已经绑定过一次了 |
| -716 | that account can only one migrate! | 平台迁移只能做一次哦；非当前登录态返回的，则可以走connect | restore属性 |
| -717 | migrate db record is wrong! | 当前设备对应的将要迁移的记录条数不正确 |
| -718 | will migrete openid is wrong! | 待绑定的openid不正确 |
| -719 | migrate is fail! | 迁移账户到其他设备失败 |
| -720 | migrate operation db exception! | 操作数据库时异常了 |
| -721 | migrate code unvailabale! | migrateCode失效 |
| -801 | notice category list error | 公告系统分类获取失败 |
| -802 | notice list empty | 公告系统分类获取失败 |
| -803 | notice category id invalid | 公告系统分类ID不合法 |
| -804 | notice lang code invalid | 公告系统语种code不合法 |
| -805 | notice region id invalid | 公告系统地区id不合法 |
| -806 | notice app-version format invalid | app version格式错误 |
| -901 | request error! | 调用接口失败，api接口错误，请检查请求串 |
| -902 | mod not exists! | 调用模块不存在，api接口错误，请检查请求串 |
| -903 | class not exists! | 调用类不存在，api接口错误，请检查请求串 |
| -904 | func not exists! | 调用函数不存在，api接口错误，请检查请求串 |
| -905 | request illegal! | 调用接口，安全鉴权码sValidKey计算失败；请检查客户端及server环境 |
| -1001 | This channel can not refresh token! | 此平台不能刷新token |
| -1101 | RET_TICKET_WRONG, |
| -1102 | params platform is error! | platform错误 |
| -1103 | get user info is failure! | 获取37wan账户信息失败 |
| -1104 | params is error! | 入参错误 |
| -1105 | game can not query Openid by sChannelId! | 游戏拒绝使用ChannelId查询相关openid信息 |
| -1106 | params gameid is undefine! | 游戏Id没有定义 |
| -1107 | no support operation | 不支持的操作 |
| -1108 | sExtToken is null!error | 第三方token值为空了 |
