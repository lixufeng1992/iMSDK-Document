## 4.4.5 支付模块(Pay)

### 基础信息

|命名空间 |调用入口 |
| :-- |:-- |
|Tencent.iMSDK | IMSDKApi.Pay |


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMPay（GameObject）上，开发者不要主动销毁该对象！</font>

### 模块使用说明

该模块主要是用于玩家购买（货币、道具、月点卡），获取营销活动信息，获取商品信息。

### 开始接入
  支付模块区分为
  Midas支付【适用除iOS官方支付外的所有第三方支付】
  及
  iOS-IAP支付【iOS官方支付】2种模式.

  * [米大师支付](pay-midas.md)
  * [iOS-IAP支付](pay-iap.md)


