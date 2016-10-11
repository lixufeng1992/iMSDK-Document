##6.4.2 Midas(iOS) 工程配置

米大师iOS支付分为两部分，**iOS应用内支付（IAP）**与**外发渠道支付**。

###IAP支付
IAP支付。由米大师直接调用iOS Store应用内付费（简称IAP, In app purchase），完成付费流程。

###接入步骤
1. 分别把米大师SDK**MidasIAPSDK.framework**和资源bundle**MidasIAPSDKRescources.bundle**引用到目前target中。![IAP支付](../../assets/Images/Midas/iap.png)
2. Xcode工程的Capability选项中添加KeychainSharing的支付专用 Group，Group ID 为 com.tencent.wsj.keystoregroup;

###注意事项
1. 环境变量开发联调阶段用test（初始化接口中environment参数），发布前切换成release，且发布前必须保证游戏 后台服务器也接入的是米大师后台的 release 环境，发布前一定要检查。


###外发渠道支付
+ 外发渠道支付。米大师通过第三方合作方支付系统，完成支付流程。

![外发渠道支付](../../assets/Images/Midas/pay_extend.png)

MidasIAPSDK.framework为米大师核心包，MidasIAPSDKRescources.bundle为米大师资源包，二者均为必选。

plugins分别为米大师不同支付外发渠道，根据实际项目需求引入不同的支付渠道即可。