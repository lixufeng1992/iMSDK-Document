## 4.4.5 支付模块(Pay)

### 基础信息

|命名空间 |调用入口 |
| :-- |:-- |
|Tencent.iMSDK | IMSDKApi.Pay |


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMPay（GameObject）上，开发者不要主动销毁该对象！</font>

### 模块使用说明

该模块主要是用于玩家购买（货币、道具、月点卡），获取营销活动信息，获取商品信息。

使用支付需要对支付系统及米大师的支付有一定的了解，这里对支付常见的术语进行说明

* 应用ID（Offer ID或App ID），在米大师进行应用注册后获取，用于标识一个应用
* 商品ID（Product ID），是指购买物品的唯一ID，在米大师后台进行配置
* 商品类型（Product Type），是指苹果内购商品类型：
  * 消费类产品（Consumables），是指可以被消耗的商品或服务，如游戏内一次性道具
  * 非消费类产品（Non-Consumables），是指永久性的商品或服务，如解锁游戏内特殊关卡
  * 包月（订阅）+自动续费（Auto-Renewable Subscriptions），是指用户购买一段时间的服务或功能，并且会自动扣费，如订阅电子杂志
  * 免费（订阅）（Free Subscriptions），用于Newsstand应用，免费但是用户可以随时取消
  * 包月（订阅）+非自动续费（Non-Renewing Subscriptions），与Auto-Renewable Subscriptions不同的地方，是到期后不会自动续费
* 支付环境（Env），是指支付环境，一般有测试（test）和正式（release）两种环境，支付时需要留意自己的支付环境
* 账户（Open ID），是指开放平台的账户ID，在iMSDK环境中，一般用登陆（Login）模块返回的OpenID字段
* 账户凭证（Open Key），是指与账户对应的校验Token，与Open ID组成用户的登录态，米大师用与于账号验证
* 支付流水（PF），是指支付流水，在支付的时候，虽然不做强制校验，但是是后续经分系统对支付进行统计的重要依据
* 会话ID（Seesion ID），米大师用该字段判断支付类型，以确认支付流程，在iMSDK环境中，一般使用hy_gameid模式
* 会话类型（Session Type），与Session ID成对出现，米大师用该字段判断具体的会话判断逻辑。在iMSDK环境中国，取值可以为“st_overseas”（海外版）、“st_dummy”中的一种，为“st_overseas”时，米大师会到iMSDK后天校验用户登录态；为“st_dummy”时，米大师不会校验登录态。

### 快速入门
1. [完成特定渠道配置](../../Channel/midas.md)  
2. 支付模块区分为  
  Midas支付【适用除iOS官方支付外的所有第三方支付】  
  及  
  iOS-IAP支付【iOS官方支付】2种模式.

  * [米大师支付](../paymidas.md)
  * [iOS-IAP支付](../payiap.md)


