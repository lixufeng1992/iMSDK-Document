

### 4.4.5.1 iOS-IAP支付

####一、快速入门
1. 代码实例

```cs
    /*
    *构造IAP支付初始化结构体：IMPayIAPInfo
    */  
    IMPayIAPInfo info = new IMPayIAPInfo();
			
			info.Local="local";
			info.OfferId="1450002792";
			info.OpenId="3bf6c30d8bfdab537bd8192d6c27560d";
			info.OpenKey="openkey";
			info.SessionId="hy_gameid";
			info.SessionType="st_dummy";
			info.Pf="desktop_m_guest-2001-iap-2001";
			info.PfKey="pfkey";
			info.Environment="test";
   
   /*
    *构造IAP支付结构体：IMPayIAPContent
    */ 
     IMPayIAPContent content = new IMPayIAPContent ();
			
			content.OfferId ="1450002792";
			content.OpenId="3bf6c30d8bfdab537bd8192d6c27560d";
			content.OpenKey = "openkey";
			content.SessionId="hy_gameid";
			content.SessionType = "st_dummy";
			content.PayItem="20";
			content.ProductId="com.tencent.imsdk.item2";
			content.Pf="desktop_m_guest-2001-iap-2001";
			content.PfKey="pfkey";
			content.IsDepositGameCoin = true;
			content.ProductType=0;
			content.ZoneId="1";
			content.VarItem="extend_column";
   
    /*
    *初始化：设置支付环境、支付预处理等
    */
    void Start() {
        /*
        *注册相关回调
        */
        IMSDKApi.PayIAP.SetRegisterCallback (this.RegisterCallback);
        IMSDKApi.PayIAP.SetOrderCallback (this.OrderCallback);
        IMSDKApi.PayIAP.SetPayCallback (this.PayCallback);
        IMSDKApi.PayIAP.SetDistributeCallback (this.DistributeCallback);
        IMSDKApi.PayIAP.SetErrorCallback (this.ErrorCallback);
        IMSDKApi.PayIAP.SetGetProductCallback (this.GetProductsCallback);

        IMSDKApi.PayIAP.Initialize(info);;//模块功能初始化
       
    }
    
    /*
    *支付
    */
    void TestPay(){
         IMSDKApi.PayIAP.Pay(content);;//支付
    }
    /*
    *拉取商品信息
    */
    void TestGetProducts(){
         List<string> products = new List<string>();
          products.Add("midas_product_1");
          products.Add("midas_product_2");
          IMSDKApi.PayIAP.GetProducts(products);
    }
     /*
    *拉取营销活动
    */
    void TestGetMP(){
           IMPayIAPContent content = new IMPayIAPContent ();			
          content.OfferId="1450002792";
          content.OpenId=	"3bf6c30d8bfdab537bd8192d6c27560d";
          content.OpenKey="openkey";
          content.SessionId="hy_gameid";
          content.SessionType="st_dummy";
          content.Pf="desktop_m_guest-2001-iap-2001";
          content.PfKey="pfkey";
          content.IsDepositGameCoin=true;
          content.ProductType=0;
          content.ZoneId="1";
          content.VarItem="extend_column";
         IMSDKApi.PayIAP.GetMP(content,callback);
    }
```

  
#### 二、支付信息类参考

* IAP支付初始化信息 <font color=blue>IMPayIAPInfo</font>    

|类型|说明|
|:--|:--|    
|public bool EnableLog = false|是否打开midas日志|     
|public string Local|支付服务器片区。"local"，中国内地；"hongkong"，香港；"canada"，加拿大|    
|public string OfferId|业务在Midas平台注册的业务id|    
|public string OpenId|iMSDK openID|   
|public string OpenKey|用户账户token，校验登录态则填对登录返回的guid_token，否则不传空就行，建议传"OpenKey"
 |    
|public string SessionId|用户账户类型，这里固定为"hy_gameid" |    
|public string SessionType|session类型，校验登录态则填"st_overseas"，否则填"st_dummy" |    
|public string Pf|平台来源，pf格式：平台字段(IEG_iTOP)-注册渠道-系统平台-安装渠道-登录渠道-GameID-OpenID-业务标识 <br />eg: IEG_iTOP-2001-iap-2011-FB-11-1000043-XD |   
|public string PfKey|支付密钥串，这里固定为"pfkey" |    
|public string Environment|支付环境，沙箱环境填"test"，现网正式环境一定改成"release"|    
|	public string Custom|额外参数 |

* IAP支付信息 <font color=blue>IMPayIAPContent</font>     

|类型|说明|   
|:--|:--|      
|public string OpenKey|用户账户token，校验登录态则填对登录返回的guid_token，否则不传空就行，建议传"OpenKey"     |    
|public string SessionId|用户账户类型，这里固定为"hy_gameid"|   
|public string SessionType|session类型，校验登录态则填"st_overseas"，否则填"st_dummy"|   
|public string ZoneId|账户分区ID。应用如果没有分区，传zoneid=1；若游戏为支持角色，zoneId需要传分区ID_角色ID|   
|public string Pf|平台来源，pf格式：平台字段(IEG_iTOP)-注册渠道-系统平台-安装渠道-登录渠道-GameID-OpenID-业务标识 <br />eg: IEG_iTOP-2001-iap-2011-FB-11-1000043-XD|    
|public string PfKey|支付密钥串，这里固定为"pfkey"|   
|public string ProductId|苹果的物品id，在Midas管理端配置 |    
|public int ProductType|苹果物品的类型。0，消费类产品，比如游戏币购买；1，非消费类产品；2，包月+自动续费；3，免费；4，包月+非自动续费|    
|public string PayItem|支付信息 <br />  1.如果应用使用道具购买类支付模式，该参数由应用方按照“物品ID*单价（单位“角”）*数量”定义 <br /> 2.如果应用使用包月类支付模式，传开通包月的月数（QQ会员这类） <br />3.如果游戏币支付模式，传充值游戏币的个数 <br />4.如果应用使用月卡类支付模式，传开通月卡天数|   
|public bool IsDepositGameCoin|是否是托管的游戏币类型|   
|public string VarItem|业务的扩展字段|   
|public string OfferId|业务在Midas平台注册的业务id|    
|public string Custom||  

#### 三、支付结果类参考
* IAP支付结果结构体 <font color=blue>IMPayIAPResult</font>

| 类型 | 说明 |    
| :-- | :-- |    
| public int Retcode | 错误码 |    
| public string RetMsg | 错误信息 |     
| public int RetBillNo | 下单成功的订单号|    
|	public int NetErrorStep|网络错误状态码|   
|	public string OpenId|iMSDK openID|  
|public string OpenKey|用户账户token，校验登录态则填对登录返回的guid_token，否则不传空就行，建议传"OpenKey" |   
|	public string SessionId|用户账户类型，这里固定为"hy_gameid"|    
|public string SessionType |session类型，校验登录态则填"st_overseas"，否则填"st_dummy"|   
|public string PayItem|支付信息 <br />  1.如果应用使用道具购买类支付模式，该参数由应用方按照“物品ID*单价（单位“角”）*数量”定义 <br /> 2.如果应用使用包月类支付模式，传开通包月的月数（QQ会员这类） <br />3.如果游戏币支付模式，传充值游戏币的个数 <br />4.如果应用使用月卡类支付模式，传开通月卡天数|   
|public string ProductId|苹果的物品id，在Midas管理端配置|   
|public string Pf|平台来源，pf格式：平台字段(IEG_iTOP)-注册渠道-系统平台-安装渠道-登录渠道-GameID-OpenID-业务标识 <br />eg: IEG_iTOP-2001-iap-2011-FB-11-1000043-XD|   
|public string PfKey|支付密钥串，这里固定为"pfkey"|   
|	public bool IsDepositGameCoin|是否是托管的游戏币类型|   
|public int ProductType|苹果物品的类型。0，消费类产品，比如游戏币购买；1，非消费类产品；2，包月+自动续费；3，免费；4，包月+非自动续费|  
|public string ZoneId|账户分区ID。应用如果没有分区，传zoneid=1；若游戏为支持角色，zoneId需要传分区ID_角色ID|   
|public string VarItem|业务的扩展字段|   
|public string BillNo|订单号|   
|public string TransactionId|票据编号|   
|public bool IsReprovide|是否补发货|   

* IAP支付获取MP结果结构体 <font color=blue>IMPayIAPMPResult</font>

| 类型 | 说明 |    
| :-- | :-- |    
| public int Retcode | 错误码 |    
| public string RetMsg | 错误信息 |      
|	public string OpenId|iMSDK openID|   
|public string OpenKey|用户账户token，校验登录态则填对登录返回的guid_token，否则不传空就行，建议传"OpenKey"|   
|	public string SessionId|用户账户类型，这里固定为"hy_gameid"|   
|public string SessionType|session类型，校验登录态则填"st_overseas"，否则填"st_dummy“|  
|public string PayItem|支付信息 <br />  1.如果应用使用道具购买类支付模式，该参数由应用方按照“物品ID*单价（单位“角”）*数量”定义 <br /> 2.如果应用使用包月类支付模式，传开通包月的月数（QQ会员这类） <br />3.如果游戏币支付模式，传充值游戏币的个数 <br />4.如果应用使用月卡类支付模式，传开通月卡天数|   
|public string ProductId|苹果的物品id，在Midas管理端配置|   
|public string Pf|平台来源，pf格式：平台字段(IEG_iTOP)-注册渠道-系统平台-安装渠道-登录渠道-GameID-OpenID-业务标识 <br />eg: IEG_iTOP-2001-iap-2011-FB-11-1000043-XD|   
|public string PfKey|支付密钥串，这里固定为"pfkey"|    
|public bool IsDepositGameCoin|是否是托管的游戏币类型|   
|public int ProductType|苹果物品的类型。0，消费类产品，比如游戏币购买；1，非消费类产品；2，包月+自动续费；3，免费；4，包月+非自动续费|    
|	public string ZoneId|账户分区ID。应用如果没有分区，传zoneid=1；若游戏为支持角色，zoneId需要传分区ID_角色ID|    
|public string VarItem|业务的扩展字段|   
|public string BillNo|订单号|   
|public string TransactionId|票据编号|    
|public bool IsReprovide|是否补发货|   
|public string GoodsInfo||    
		
#### 四、支付接口参考
* 支付回调 

| 类型 | 说明 |
| :-- | :-- |
| public delegate void PayCallback(IMPayResult result) |IAP支付回调函数，返回支付结果结构体 |      
|public delegate void IAPGetMPCallback(IMPayIAPMPResult result)|IAP拉取营销活动|    
|public delegate void GetProductInfoCallback(string result)|IAP获取商品列表|      

* IAP接口说明

|方法名 | 方法说明 |
| :-- | :-- | 
|public bool Initialize(IMPayIAPInfo info)| IAP支付初始化|    
|public string GetPf(string openId="1000000", string registerChannel="2001", string setupChannel="2011", string appCode="AppCode") |IAP支付获取pf|  
|public void Pay(IMPayIAPContent content)|IAP支付|  
|	public void GetProducts(List\<string\>productIds)|IAP获取商品信息|    
|public void GetMP (IMPayIAPContent content,IAPGetMPCallback callback = null)|IAP拉取营销活动|   
|public void SetRegisterCallback(PayCallback callback)|设置注册回调|  
|	public void SetOrderCallback(PayCallback callback)| 设置定单回调|   
|	public void SetDistributeCallback(PayCallback callback)|设置发贷回调|    
| public void SetPayCallback(PayCallback callback)|设置支付回调| 
|public void SetErrorCallback(PayCallback callback)|设置失败回调|    
|public void SetGetProductCallback(GetProductInfoCallback callback)|设置获取商品信息回调|    
