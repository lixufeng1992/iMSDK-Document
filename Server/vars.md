## 7.5 各个平台变量名对应关系表

| **Imsdk serverUnity3DIosAndroid说明** |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- |
| code | RetCode | errCode | retCode | Imsdk返回值 |
| desc | ErrorMsg | message | retMsg | Imsdk返回信息提示 |
| iOpenid | OpenId | guid\_open\_id | openId | 游戏内UId |
| sInnerToken | GuidToken | guid\_token | guidToken | Imsdk token |
| iGuid | Guid | guid | guid | 全球统一标识id |
| iChannel | ChannelId | guid\_channel\_id | channelId | 登录渠道Id |
| iGameId | GameId | guid\_game\_id | gameId | 游戏业务Id |
| sChannelId |  | channel\_userid | channelUserId | 第3方用户Id |
| iExpireTime | GuidTokenExpire | guid\_token\_expire | guidTokenExpire | Imsdk token有效期 |
| sUserName | GuidUserNick | guid\_user\_nick | guidUserNick | 用户名 |
| sBirthdate | GuidUserBirthday | guid\_user\_birthday | guidUserBirthday | 出生日期\(1987-2-23 11:33:33\) |
| iGender | GuidUserSex | guid\_user\_gender | guidUserSex | 性别\(int\) 0未定义,1男,2女 |
| sPictureUrl | GuidUserPortrait | guid\_user\_portrait | guidUserPortrait | 头像 |
| sExtToken |  | channel\_token | channelToken | 第3方token |
| iExtTokenExpireTime |  | channel\_expire | channelTokenExpire | 第3方token有效期 |

