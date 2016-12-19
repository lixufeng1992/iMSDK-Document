#
# 8.5 社交渠道一览表
| 渠道id | 渠道名称 | 渠道简称 | 子渠道简称 | 备注 |
| :-- | :-- | :-- | :-- |:-- |
| 1 | Facebook | FB | | |
| 2 | GameCenter | GC | | |
| 3 | Google | GG | | |
| 4 | WeChat | WX | | |
| 5 | Guest | GU | | |
| 6 | Zalo | ZL |ZL  ZM  ZGU | Zalo内部Zalo渠道 Zalo内部Zing渠道  Zalo内部游客渠道 |
| 7 | 37Ｗeb | 37W | | |
| 8 | SQW  GM | SQW  GM | | 37wan  G妹 |
| 9 | Link | LK | | |
| 10 | Viber | VB | | |
| 11 | OasGames | OAS | | |
| 12 | FLKK | FLKK | | 飞流（封装了KaKao渠道） |
| 13 | Garena | GRN | GRN_Gas  GRN_BT  GRN_GU | Garena内部Gas渠道  Garena内部BeeTalk渠道  Garena内部游客渠道 |
| 14 | VK | VK | | |
| 15 | Toy | Toy | Toy_GU  Toy_FB  Toy_TW  Toy_EM  Toy_GO  Toy_DE | Toy内部游客渠道  Toy内部Facebook渠道  Toy内部Twitter渠道  Toy内部Email渠道  Toy内部Google Plus渠道  Toy默认登录渠道 |
| 16 | Efun | Efun | | |
| 17 | KAKAO | KK | | |
| 18 | MTO | | | |
| 19 | Stove | | | |

- 渠道id：channelid
- 渠道名称：客户端登录时设置的渠道名
- 渠道简称：支付pf使用到的渠道缩写
- 子渠道简称：支付pf使用到的子渠道缩写

>备注：pf中登录渠道优先使用子渠道简称，如果子渠道简称没有则使用渠道简称

----------
## 支付pf格式

平台字段(IEG_iTOP)-注册渠道-系统平台-安装渠道-登录渠道-GameID-OpenID-业务标识
比如：IEG_iTOP-2001-iap-2011-FB-11-1000043-XD

----------
## tLOG对应gameappid标识
渠道标识缩写(大写)_海外平台GameID
如：
FB_1020
GC_1020
GG_1020
WX_1020
GU_1020