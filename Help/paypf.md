## 8.6 支付PF字段填写规则

PF示例：

>IEG_iTOP-2001-android-2011-GU-1100-123456-IMSDK

其中：

* IEG_iTOP 为固定头
* 2001 为注册渠道，默认值为 “2001”
* android 为设备类型，Android 填 “android”， iOS 填 “iap”
* 2011 为安装渠道，默认值为 “2011”
* GU 登录渠道简称，可以参考[渠道简称列表](shortchannel.md)
* 1100 为 iMSDK 游戏 ID
* 123456 为 iMSDK OpenID
* IMSDK 为业务简称
