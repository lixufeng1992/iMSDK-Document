

### 4.4.5.1 iOS-IAP支付

####快速入门
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

  
#### 参考

* IAP支付初始化信息 <font color=blue>IMPayIAPInfo</font>    

|类型|说明|
|:--|:--|    
|public bool EnableLog = false|是否打开midas日志|     
|public string Local|IDC|    
|public string OfferId|offer ID|    
|public string OpenId|iMSDK openID|   
|public string OpenKey| |    
|public string SessionId| |    
|public string SessionType| |    
|	public string Pf||   
|public string PfKey| |    
|public string Environment||    
|	public string Custom| |

* IAP支付信息 <font color=blue>IMPayIAPContent</font>     

|类型|说明|   
|:--|:--|      
|public string OpenKey||    
|public string SessionId||   
|public string SessionType||   
|public string ZoneId||   
|public string Pf||    
|public string PfKey||   
|public string ProductId||    
|public int ProductType||    
|public string PayItem||   
|public bool IsDepositGameCoin||   
|public string VarItem||   
|public string OfferId||    
|public string Custom||  

* IAP支付结果结构体 <font color=blue>IMPayIAPResult</font>

| 类型 | 说明 |    
| :-- | :-- |    
| public int imsdkRetcode | 错误码 |    
| public string imsdkRetMsg | 错误信息 |     
| public int thirdRetcode | 第三方错误码 |    
| public string thirdRetMsg | 第三方错误信息 |   
| public int RetBillNo | |    
|	public int NetErrorStep||   
|	public string OpenId||  
|public string OpenKey||   
|	public string SessionId||    
|public string SessionType ||   
|public string PayItem||   
|public string ProductId||   
|public string Pf||   
|public string PfKey||   
|	public bool IsDepositGameCoin||   
|public int ProductType||  
|public string ZoneId||   
|public string VarItem| |   
|public string BillNo|  |   
|public string TransactionId||   
|public bool IsReprovide||   

* IAP支付获取MP结果结构体 <font color=blue>IMPayIAPMPResult</font>

| 类型 | 说明 |    
| :-- | :-- |    
| public int imsdkRetcode | 错误码 |    
| public string imsdkRetMsg | 错误信息 |     
| public int thirdRetcode | 第三方错误码 |    
| public string thirdRetMsg | 第三方错误信息 |     
|	public string OpenId||   
|public string OpenKey||   
|	public string SessionId||   
|public string SessionType||  
|public string PayItem||   
|public string ProductId||   
|public string Pf||   
|public string PfKey||    
|public bool IsDepositGameCoin||   
|public int ProductType||    
|	public string ZoneId||    
|public string VarItem||   
|public string BillNo||   
|public string TransactionId||    
|public bool IsReprovide||   
|public string GoodsInfo||    
		

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
|	public void GetProducts(List<string>productIds)|IAP获取商品信息|    
|public void GetMP (IMPayIAPContent content,IAPGetMPCallback callback = null)|IAP拉取营销活动|   
|public void SetRegisterCallback(PayCallback callback)|设置注册回调|  
|	public void SetOrderCallback(PayCallback callback)| 设置定单回调|   
|	public void SetDistributeCallback(PayCallback callback)|设置发贷回调|    
| public void SetPayCallback(PayCallback callback)|设置支付回调| 
|public void SetErrorCallback(PayCallback callback)|设置失败回调|    
|public void SetGetProductCallback(GetProductInfoCallback callback)|设置获取商品信息回调|    
