##6.4.2 Midas(iOS) 工程配

米大师iOS支付分为两部分，**iOS应用内支付（IAP）**与**外发渠道支付**。

###IAP支付
IAP支付。米大师直接调用iOS Store应用内付费（简称IAP, In app purchase），完成支付流程。工程配置需要分别把米大师SDK**MidasIAPSDK.framework**和资源bundle**MidasIAPSDKRescources.bundle**引用到目前target中。![IAP支付](../Images/Midas/iap.png)

###外发渠道支付
+ 外发渠道支付。米大师通过第三方合作方支付系统，完成支付流程。!(外发渠道支付)(../Images/Midas/iap.png)