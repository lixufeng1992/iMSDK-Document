## 7.2 iMSDK Server 错误码定义

1 =&gt; "success", \/\/成功

2 =&gt; 'connect this sns channel!', \/\/挂载这个社交渠道，请调用reconnect接口

3 =&gt; 'restore this sns account!', \/\/恢复这个社交渠道，请调用restore接口

4 =&gt; 'the same openid!', \/\/相同的openid无需恢复

5 =&gt; 'need google authcode', \/\/需要google提供授权

6 =&gt; 'migrate fail, suggest request restore interface! restore return sns account!', \/\/请走restore接口，使用恢复的方式， 恢复数组中的openid到当前设备上

-1 =&gt; "failure", \/\/失败

-2 =&gt; 'access limit! wait a moment to try', \/\/请求太过频繁了，请过一会再登录

-101 =&gt; "ChannelHashId query guid is failure!", \/\/ChannelHashId2Guid失败

-102 =&gt; "Guid query ChannelHashId failure", \/\/Guid2ChannelHashId失败

-103 =&gt; "tag Guid table record delete failure", \/\/标识Guid表记录被删除失败

-104 =&gt; "tag ChannelHashId table record delete failure", \/\/标识ChannelHashId表记录被删除失败

-105 =&gt; "add Guid table record is failure", \/\/添加Guid表记录失败

-106 =&gt; "add ChannelHashId table record is failure", \/\/添加ChannelHashId表记录失败

-107 =&gt; "no params ChannelHashId", \/\/没有ChannelHashId

-108 =&gt; "no params ChannelId", \/\/没有传入ChannelId

-109 =&gt; "no params Guid", \/\/没有传入Guid

-110 =&gt; "Guid is un Avali", \/\/guid无效

-111 =&gt; "Channel is un avail", \/\/渠道无效

-112 =&gt; "Sex is un avail", \/\/性别无效

-113 =&gt; "Status is un avail", \/\/状态无效

-114 =&gt; "UserName is un avail", \/\/用户昵称无效

-115 =&gt; "Modify user nicename is failure", \/\/修改Guid表记录用户昵称失败

-116 =&gt; "Modify user Sex is failure", \/\/修改Guid表记录用户性别失败

-117 =&gt; "Modify user Age is failure", \/\/修改Guid表记录用户年龄失败

-118 =&gt; "Modify user Ip is failure", \/\/修改Guid表记录IP失败

-119 =&gt; "modify Guid table record is failure", \/\/修改Guid表记录失败

-120 =&gt; "modify ChannelHashId table record is failure", \/\/修改ChannelHashId表记录失败

-121 =&gt; "add user record is failure", \/\/添加用户失败

-122 =&gt; "ChannelId no play this game", \/\/ChannelHashId暂时没有玩过这个游戏

-123 =&gt; "ChannelId's Openid error", \/\/ChannelHashId查到的Openid与传参不匹配

-124 =&gt; "openid input is eaqual to db or src, no need to change", \/\/ChannelHashId查到的Openid与传参一致，无需修改

-125 =&gt; "update guid userInfo failure", \/\/更新iguid表时失败

-126 =&gt; "not a short gameId game", \/\/非32位短帐号游戏

-127 =&gt; "old openid empty", \/\/在oldOpenid表中没有对应记录

-128 =&gt; "delete openid failure" , \/\/删除openid失败

-129 =&gt; "add openid failure" , \/\/添加openid到db失败

-130 =&gt; "delete Guid failure" , \/\/删除openid失败

-131 =&gt; "update Openid failure" , \/\/删除openid失败

-132 =&gt; "guid is disable status!", \/\/GUID为停用状态

-133 =&gt; "guid is delete status!", \/\/GUID为删除状态

-134 =&gt; "openid is disable status!", \/\/Openid为停用状态

-135 =&gt; "openid is delete status!", \/\/Openid为删除状态

-136 =&gt; 'no openid input params!', \/\/没有传入openid参数

-201 =&gt; "verify failure!", \/\/facebook鉴权失败

-202 =&gt; "user account is not available!", \/\/用户状态为停用

-203 =&gt; "user account was deleted!", \/\/用户状态为删除态

-204 =&gt; "user session is failure!", \/\/用户登录态过期

-205 =&gt; "user session is error!", \/\/错误的用户登录态

-206 =&gt; "user session operation is failure", \/\/保存用户登录态到memcache失败

-207 =&gt; "get user session is failure!", \/\/获取用户登录态到memcache失败

-208 =&gt; "del user session is failure!", \/\/删除用户登录态到memcache失败

-209 =&gt; "no appid params or no appsecret params!", \/\/没有传入APPID或者不存在appid对应；的appsecret

-210 =&gt; "facebook verify failure!", \/\/facebook鉴权失败

-211 =&gt; "WEIXIN verify failure!", \/\/WEIXIN鉴权失败

-212 =&gt; "apple verify failure!", \/\/apple鉴权失败

-213 =&gt; "google verify failure!", \/\/google鉴权失败

-214 =&gt; "guest mod set failure!", \/\/使用游客模式失败

-215 =&gt; "verify params is error!", \/\/鉴权传递参数错误

-216 =&gt; "facebook request interface unset", \/\/facebook请求接口不存在

-217 =&gt; "facebook request is failure", \/\/facebooke请求失败

-218 =&gt; "guest login failure!", \/\/启用游客模式失败

-219 =&gt; "Invalid request!", \/\/请求无效

-220 =&gt; "Invalid param gameid", \/\/businessid不是有效的参数

-221 =&gt; "add openid to channelId failure", \/\/添加用户Guid到游戏关系失败

-222 =&gt; "add channelid to openid failure", \/\/添加CHANNELID到游戏关系失败

-223 =&gt; "need authorize openid play this game", \/\/guid有到此游戏的权限， 但是openid之前没有玩过此游戏；

-224 =&gt; "add user to gameid failure!", \/\/添加用户到玩过此游戏的对应关系失败

-225 =&gt; "channel param is error!", \/\/平台参数错误或无效

-226 =&gt; "params is error!", \/\/参数错误

-227 =&gt; "params gameid is error!", \/\/传参gameid错误

-228 =&gt; 'update openid failure' , \/\/更新用户Openid失败

-229 =&gt; 'check login failure' , \/\/isLogin返回失败

-230 =&gt; 'get weixin UserInfo failure!', \/\/通过accesstoken和openid去获取用户信息失败

-231 =&gt; 'RET\_USERVERIFY\_SESSION\_ERROR', \/\/用户第3方鉴权信息kv操作失败

\/\/-232 =&gt; 'binding the wrong channel', \/\/绑定渠道错误

-233 =&gt; 'update token info failure!', \/\/更新token信息失败

-234 =&gt; "weixin req access\_token's expire\_in is failure!", \/\/微信返回token有效期失败

-235 =&gt; 'weixin req Openid is failure', \/\/微信返回OPenid失败

-236 =&gt; 'weixin req token is failure', \/\/微信返回token失败

-237 =&gt; 'weixin req refresh\_token is failure!', \/\/微信返回refresh\_token失败

-238 =&gt; 'facebook token is Invalid', \/\/facebook token 过期

-239 =&gt; 'google token is Invalid', \/\/google token 过期

-240 =&gt; 'weixin token is Invalid', \/\/weixin token 过期

-241 =&gt; 'facebook appid info is error', \/\/facebook gameid对应appInfo 配置错误

-242 =&gt; 'google appid info is error', \/\/google gameid对应appInfo 配置错误

-243 =&gt; 'weixin appid info is error', \/\/weixin gameid对应appInfo 配置错误

-244 =&gt; 'weixin get relationship failure!', \/\/weixin 获取好友关系链失败

-245 =&gt; 'get ticket failure!', \/\/获取ticket失败

-246 =&gt; "request illegal!", \/\/非法请求

-247 =&gt; "not need update accesstoken!", \/\/更新token失败或不需要更新token信息

-248 =&gt; "Zalo verify is failure!", \/\/Zalo鉴权失败

-249 =&gt; "Zalo getfriends is failure!", \/\/Zalo鉴权失败

-250 =&gt; "Zalo appinfo get failure!", \/\/zalo应用信息拉取失败

-251 =&gt; "no params openid", \/\/没有传入OPENID

-252 =&gt; "no params guid", \/\/没有传入GUID

-253 =&gt; "no params iChannelHashId", \/\/没有传入iChannelHashId

-254 =&gt; "params iChannelHashId is illegal", \/\/iChannelHashId illegal

-255 =&gt; "Zalo verify Guest channel is failure!", \/\/Zalo鉴权zalo游客模式失败

-256 =&gt; "37wan verify is failure!", \/\/37wan鉴权失败

-257 =&gt; "get return info failure!", \/\/拿取返回信息失败

-258 =&gt; "check and login is failure!", \/\/检查并登录

-259 =&gt; "can not support this channel or channel unset!", \/\/不支持此渠道或渠道无效

-260 =&gt; "google verify info memcd get failure!", \/\/google鉴权信息cache获取失败

-261 =&gt; "Link verify is failure!", \/\/link鉴权失败

-262 =&gt; "oauth config is error or no info!", \/\/应用配置信息错误或没有配置

-263 =&gt; "sign cannot use many times!", \/\/37wan不能重复使用ssign

-264 =&gt; "Fb had other user relation, can not bind this user!", \/\/App37wan FB存在openid了，不能在进行绑定到别的37Wan上

-265 =&gt; 'zalo token unexpiretime', \/\/zalo token 过期, 建议前端重新登录授权

-266 =&gt; 'oas sign cannot use many times!', \/\/oas不能重复使用ssign

-267 =&gt; 'oasgames verify is failure!', \/\/oasgames鉴权失败

-268 =&gt; 'viber verify is failure!', \/\/viber鉴权失败

-269 =&gt; 'feiliu verify is failure!', \/\/feiliu鉴权失败

-270 =&gt; 'viber get relationship failure!', \/\/viber获取好友关系链失败

-271 =&gt; 'garena verify failure', \/\/garena 鉴权失败

-272 =&gt; 'vk verify failure', \/\/vk verify failure

-273 =&gt; 'toy verify failure', \/\/toy verify failure

-274 =&gt; 'efun verify failure', \/\/efun verify failure

-275 =&gt; 'kakao verify failure', \/\/kakao verify failure

-276 =&gt; 'MTO verify failure', \/\/kakao verify failure

-277 =&gt; 'stove game access token verify failure', \/\/STOVE game\_access\_token verify failure

-278 =&gt; 'get or set stove character failure', \/\/get or set stove character failure

-301 =&gt; "bind relationship is failure,because openid unset", \/\/绑定失败,有可能的原因是openid被删除或者不存在

-302 =&gt; "you already bound this channel!", \/\/之前绑定过，不能再进行绑定了

\/\/-303 =&gt; "bind: get session info error", \/\/从session中获取信息失败

\/\/-304 =&gt; "bind: gameId or openid isn't equal to session", \/\/从session中获取信息与传参不一致

-305 =&gt; "bind: usersission wrong", \/\/session 空

\/\/-306 =&gt; "bind: usersission to array error", \/\/session转化成数组错误

-307 =&gt; "bind: openid exist, binding forbidden", \/\/已经存在对应openid，不允许绑定

-308 =&gt; "bind: guid exist, binding forbidden", \/\/已经存在对应guid，不允许绑定

\/\/-309 =&gt; "bind: add guid&openid for binding error", \/\/添加用户guid及openid绑定关系

-310 =&gt; "bind: innertoken error", \/\/用户的内部token错误

\/\/-311 =&gt; "bind: delete openid error", \/\/删除绑定关系失败

-312 =&gt; 'binding the wrong channel', \/\/绑定渠道错误

-313 =&gt; "params gameid is error!", \/\/传参gameid错误

-314 =&gt; "params openid is error!", \/\/传参openid错误

\/\/-315 =&gt; "params BindAccessToken is error!", \/\/外部token传参错误

\/\/-316 =&gt; "bind: add guid to db error", \/\/添加guid到db失败

-317 =&gt; "bind: params guid is error!", \/\/传参guid错误

-318 =&gt; "unbind: params channel is error!", \/\/解绑传参channel错误

-319 =&gt; 'garena\_bindurl is test fail!', \/\/garena绑定判断失败

-401 =&gt; "no params sAppChannelId", \/\/没有传入APP对应的CHANNELID或者不存在appid对应；的appsecret

-402 =&gt; "get FriendList is failure!", \/\/获取好友列表失败

-403 =&gt; "This channel no friend list!", \/\/此平台无好友关系链

-404 =&gt; "no sAppChannelId to get Friendlist!", \/\/没有app对应的channelid

-405 =&gt; 'sns token is failure!', \/\/第3方token失效

-501 =&gt; "tags params is error!", \/\/Tags入参错误

-502 =&gt; "add tag to tb\_openid2tag failure!", \/\/tag 插入到openid2tag表失败

-503 =&gt; "add tag to tb\_tag2openid failure!", \/\/tag 插入到tag2oepnidb失败

-504 =&gt; "get tagid list failure!", \/\/获取tagidlist 失败

-505 =&gt; "query tag is failure!", \/\/查询tag失败

-506 =&gt; "this openid has no tag", \/\/此玩家的没有tag

-507 =&gt; "no push record!", \/\/此玩家没有tag信息

-508 =&gt; "push personal taginfo query failure!", \/\/查询此玩家对应tag信息失败

-509 =&gt; "push query openid by tag and gameid is failure!", \/\/查询tag对应游戏的玩家失败

-510 =&gt; "push sql to Gameid2tag failure!", \/\/插入到GameId分表失败

-601 =&gt; "paras email is illegal!", \/\/入参email不合法

-602 =&gt; "logind innertoken or Openid params is error!",

-603 =&gt; "write personal info is failure!", \/\/写入个人信息失败

-604 =&gt; "no Personal info!", \/\/没有查询到个人信息

-700 =&gt; 'params sGuestId is error', \/\/传入的登录态和sGuestId不匹配

-701 =&gt; 'can not restore to strong relation account on!', \/\/不能恢复到存在强关联关系的账户

-702 =&gt; 'save confirmcode is fail!', \/\/保存用户确认码到memcache失败

-703 =&gt; 'get confirmcode is fail!', \/\/获取用户确认码到memcache失败

-704 =&gt; 'del confirmcode is fail!', \/\/删除用户确认码到memcache失败

-705 =&gt; 'ConfireCode unavail', \/\/用户确认码失效

-706 =&gt; 'no openid reconnect fail!', \/\/当前openid不存在此渠道，直接挂载此渠道失败

-707 =&gt; 'had openid reconnect fail!', \/\/当前openid存在此渠道，再次挂载此渠道时操作失败

-708 =&gt; 'openid reconnect fail!\[exception\]', \/\/当前openid存在此渠道，异常的失败

-709 =&gt; 'connect or restore model select error!', \/\/模式选择错误，比如强关联模式，选成了弱关联模式处理了

-710 =&gt; 'no openid restore fail!', \/\/当前openid不存在此渠道，snsOpenid也不存在，直接关联此渠道失败

-711 =&gt; 'had openid restore fail!', \/\/当前登录态存在这个渠道的强关联，sns不存在openid时，不用恢复

-712 =&gt; 'openid restore fail!\[exception\]', \/\/当前openid存在此渠道，异常的失败

-713 =&gt; 'platform is Err!', \/\/错误的平台

-714 =&gt; 'is not sns model relation!', \/\/不是强SNS社交模式游戏

-715 =&gt; 'this account can only one migrate!', \/\/平台迁移只能做一次哦；当前登录态返回的，返回失败，原因是已经绑定过一次了

-716 =&gt; 'that account can only one migrate!', \/\/平台迁移只能做一次哦；非当前登录态返回的，则可以走connect =&gt; restore属性

-717 =&gt; 'migrate db record is wrong!', \/\/当前设备对应的将要迁移的记录条数不正确

-718 =&gt; 'will migrete openid is wrong!', \/\/待绑定的openid不正确

-719 =&gt; 'migrate is fail!', \/\/迁移账户到其他设备失败

-720 =&gt; 'migrate operation db exception!', \/\/操作数据库时异常了

-721 =&gt; 'migrate code unvailabale!', \/\/migrateCode失效

-722 =&gt; 'migrete Code had strong sns channel, cannot migrate!', \/\/migrateCode强关联关系渠道， 不能迁移

-723 =&gt; 'devices had this channel snsinfo, can not recover, please use snsrestore！', \/\/recover时， guest已经有这个sns渠道的信息， 则不能recover过去

-724 =&gt; 'donot support weak sns for recover at none deviceId openid.', \/\/recover时， guest不存在账户，sns存在账户，但因为是弱关联关系， 则不能recover过去

-725 =&gt; 'cannot disconnect same channel', \/\/disconnect，不能断开和当前登录态相同的渠道，或游客渠道

-726 =&gt; 'the same platform!', \/\/同一平台不能迁移，请引导绑定gc\|gp， 走restore

-727 =&gt; 'migrate condition is fail, please connect GP\|GC!', \/\/migrate的前提条件不满足，请先connect渠道GP

-728 =&gt; 'migrate condition is fail, please connect GP\|GC', \/\/migrate的前提条件不满足，请先connect渠道GC

-801 =&gt; "notice category list error", \/\/公告系统分类获取失败

-802 =&gt; "notice list empty", \/\/公告系统分类获取失败

-803 =&gt; "notice category id invalid", \/\/公告系统分类ID不合法

-804 =&gt; "notice lang code invalid", \/\/公告系统语种code不合法

-805 =&gt; "notice region id invalid", \/\/公告系统地区id不合法

-806 =&gt; "notice app-version format invalid", \/\/app version格式错误

-901 =&gt; 'request error!', \/\/调用接口失败，api接口错误，请检查请求串

-902 =&gt; 'mod not exists!', \/\/调用模块不存在，api接口错误，请检查请求串

-903 =&gt; 'class not exists!', \/\/调用类不存在，api接口错误，请检查请求串

-904 =&gt; 'func not exists!', \/\/调用函数不存在，api接口错误，请检查请求串

-905 =&gt; 'request illegal!', \/\/调用接口，安全鉴权码sValidKey计算失败

-906 =&gt; 'access denied', \/\/无权访问，ip不在白名单

-1001 =&gt; "This channel can not refresh token!", \/\/此平台不能刷新token

-1101 =&gt; "RET\_TICKET\_WRONG",

-1102 =&gt; "params platform is error! or login new account request access limit!", \/\/platform错误或者在新账户创建是操作太频繁导致

-1103 =&gt; "get user info is failure!", \/\/获取37wan账户信息失败

-1104 =&gt; "params is error!", \/\/入参错误

-1105 =&gt; "game can not query Openid by sChannelId!", \/\/游戏拒绝使用ChannelId查询相关openid信息

-1106 =&gt; "params gameid is undefine!", \/\/游戏Id没有定义

-1107 =&gt; "no support operation", \/\/不支持的操作

-1108 =&gt; "sExtToken is null!error", \/\/第三方token值为空了

-1200 =&gt; 'There is no config for this game and platform', \/\/该游戏没有相关动态配置

