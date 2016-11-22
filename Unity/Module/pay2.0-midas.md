
### 4.4.5.1 米大师支付

####一、快速入门
1. [完成特定渠道配置](../../Channel/midas.md)   
2. 代码实例

```cs
    /*
    *构造支付预处理结构体：IMPayMidasPrepareContent
    */  
    IMPayMidasPrepareContent CreatePrepareContent(){
      IMPayMidasPrepareContent prepareContent = new IMPayMidasPrepareContent();
      prepareContent.OfferId = "1450005285";//支付应用ID，又称为AppId，从米大师获取
      prepareContent.OpenId = openId;//用户 OpenID，取值为登录（Login）模块返回的 OpenID
      prepareContent.OpenKey = accessToken;//用户校验凭证，取值为登录（Login）模块返回的 GuidToken
      prepareContent.SessionId = "hy_gameid"; // 登陆态票据类型，默认固定为 "hy_gameid"
      prepareContent.SessionType = "st_overseas"; //登陆态票据类型，"st_overseas"表示支付时需校验登录态,"st_dummy"表示不校验登录态
      prepareContent.Pf = "IEG_iTOP-2001-iap-2011-Zalo-1011-1000065-XD";//米大师支付流水，可以通过GetPF方法获取
      prepareContent.PfKey = "pfKey";//使用iMSDK支付时，固定取值为“pfKey”
      prepareContent.ZoneId = "1";//游戏服务器大区id,游戏不分大区则默认zoneId ="1"，在米大师管理端进行配置获取
  }
   
   /*
    *构造支付结构体：IMPayMidasContent
    */ 
   IMPayMidasContent GetPayMidasContent(){
          IMPayMidasContent content = new IMPayMidasContent ();
          content.OfferId = "1450005285";//支付应用ID，又称为AppId，从米大师获取
          content.OpenId = openId;//用户 OpenID，取值为登录（Login）模块返回的 OpenID
          content.OpenKey = accessToken;//用户校验凭证，取值为登录（Login）模块返回的 GuidToken
          content.SessionId = "hy_gameid"; // 登陆态票据类型，默认固定为 "hy_gameid"
          content.SessionType = "st_overseas"; // 登陆态票据类型，"st_overseas"表示支付时需校验登录态,"st_dummy"表示不校验登录态
          content.ZoneId = "1";//游戏服务器大区id,游戏不分大区则默认zoneId ="1"，在米大师管理端进行配置获取
          content.Pf = "IEG_iTOP-2001-iap-2011-Zalo-1011-1000065-XD";//米大师支付流水，可以通过GetPF方法获取
          content.PfKey = "pfKey";//使用iMSDK支付时，固定取值为“pfKey”
          content.ProductId = "midas_product_1";//米大师商品ID，用于标识一件商品，在米大师管理端进行配置获取，请注意与BuyGameOrGoodsOrMonth配合使用
          content.ResId = "unipay_abroad_iconload";//【Android特有】购买货币图标文件资源，需要放在米大师工程目录的 res/drawable-??/. 目录下。如果图片文件名称为 unipay_abroad_iconload.png， 则这里填写“unipay_abroad_iconload”
          content.Country = "US";//投放国家的国家编码，如：“CN”、“HK”、“US”等,在米大师管理端进行配置获取
          content.CurrencyType = "USD";//投放国家货币类型简称，如： “CNY”（人民币）、“HKD”（港币）、“USD”（美金）等,在米大师管理端进行配置获取
          content.BuyGameOrGoodsOrMonth = "Goods";//Game:钻石 Goods:道具 Month:月卡
          //支付渠道,设置为"all"则支持所有支付渠道，即打开midas商城页//【Android特有】,选择购买类型，Game:购买钻石 Goods:购买道具 Month:购买月卡，请注意与ProductId配合使用，购买类型不同，ProductId也会不同
          content.payChannel = "all";//设置支付渠道,一般无需设置，表现为拉起SetChannel时指定的支付渠道界面，特殊的当设置为"all"时则表示支持所有支付渠道，表现为拉起midas商城界面，midas商城包含所有已注册支付渠道。
          return content;
   }
   
    /*
    *初始化：设置支付环境、支付预处理等
    */
    void Start() {
    	List<string> channels = new List<string>();
	channels.Add("MidasGoogle");
        IMSDKApi.PayOversea.Initialize(channels);//模块功能初始化
	
        IMSDKApi.PayOversea.SetChannel("MidasGoogle");//设置渠道
        IMSDKApi.PayOversea.SetEnv("test");//设置沙箱环境
        IMSDKApi.PayOversea.EnableDebugLog(true);//设置开启日志
        IMSDKApi.PayOversea.SetIDC("local");//设置IDC
        IMSDKApi.PayOversea.Prepare(CreatePrepareContent());//支付预处理
    }
    
    /*
    *支付
    */
    void TestPay(){
        IMSDKApi.PayOversea.Pay(GetPayMidasContent(),PayMidasCallback);//支付
    }
    
    /*
    *GetProducts:获取商品或营销活动信息(从Midas后台获取)
    */
    void TestGetProducts(){
       IMPayMidasContent paycontent  = GetPayMidasContent();
       IMSDKApi.PayOversea.GetProducts(paycontent, MidasProdctCallback);
    }
    
    /*
    *GetProducts:获取商品或营销活动信息(从Google后台获取),【Android特有】
    */
    void TestGetProductsFromGoogleSrv(){
       List<IMMidasProductContent> list = new List<IMMidasProductContent>();
       list.Add("your_google_productId1");
       list.Add("your_google_productId2");
       ...
      IMSDKApi.PayOversea.GetProducts(list, MidasProdctCallback);
    }
```


####二、 支付流程说明

* 米大师支付分为初始化（Initialize）、设置支付渠道（SetChannel）、设置支付环境（SetEnv）、设置支付区域（SetIDC）、支付准备（Prepare）、支付（Pay）这几个步骤

  1.初始化，在支付流程中，必须先调用初始化接口才能调用其他函数，包括支付和设置支付渠道
  
    ```cs
    IMSDKApi.PayOversea.Initailize( YOUR_GOOGLE_PUBLIC_KEY );
    ```    
	
  2.设置支付渠道，米大师支付流程中，支付渠道都是“Midas”开头的字符串

    ```cs
    IMSDKApi.PayOversea.SetChannel( YOUR_PAY_CHANNEL );
    ```      

  3.【可选】打开支付日志，测试时建议打开日志，便于定位问题，测试完成后可以关闭

    ```cs
    IMSDKApi.PayOversea.EnableDebugLog( YOUR_CHOICE );
    ```       

  4.设置支付环境，支付环境一般为测试（“test”）或者正式环境（“release”）

    ```cs
    IMSDKApi.PayOversea.SetEnv( YOUR_PAY_ENVIRONMENT ); 
    ```    

  5.设置支付服务器区域，一般根据自己游戏需要，选择合适的支付区域

    ```cs
    IMSDKApi.PayOversea.SetIDC( YOUR_PAY_AREA );
    ```    
  

  6.支付准备，该步骤一般在登录操作完成后进行

    ```cs
    IMSDKApi.PayOversea.Prepare( YOUR_PREPARE_CONTENT );
    ```     
  

  7.支付，只有完成上述步骤后，才能调用支付方法
    
    ```cs
    IMSDKApi.PayOversea.Pay( YOUR_PAY_CONTENT, YOUR_PAY_CALLBACK );
    ```      
   
  
  
####三、支付信息参考

* 支付prepare信息结构体 <font color=blue>IMPayMidasPrepareContent</font>

| 变量 | 说明 |    
| :-- | :-- |             
| public string OfferId|【重要】支付应用ID,从米大师获取|    
| public string OpenId | 用户 OpenID，取值为登录（Login）模块返回的 OpenID |
| public string OpenKey | 用户校验凭证，取值为登录（Login）模块返回的 GuidToken |
| public string SessionId | 米大师会话ID，取值为“hy_gameid” |
| public string SessionType | 米大师会话类型，取值为“st_overseas”（校验登录态）、“st_dummy”（不校验登录态）中的一种 |
| public string Pf | 米大师支付流水，可以通过GetPF方法获取 |
| public string PfKey | 使用iMSDK支付时，取值为“pfKey” |
| public string ZoneId | 米大师的大区ID，该ID需要在米大师管理端进行配置 |
| public string Env | 【iOS】【重要】米大师支付环境，取值为“test”（测试）、“release”（正式）中的一种 |
| public string Local | 【iOS】【重要】米大师支付区域，该值需要根据游戏的发布地区确认，如：“hongkong”（香港） |
| public string SessionChannel  | 【iOS】登录渠道，与登录模块中的渠道ID定义保持一致，如：1（Facebook）、2（GameCenter）、3（Google Play & Plus）、4（Wechat）、5（iMSDK Guest）等等 |   
 
><font color=green>说明：Env和Local为iOS专有字段，如果iOS环境下已经调用了SetEnv方法，这个字段可以不填</font>


* 支付信息结构体 <font color=blue>IMPayMidasContent</font>

| 变量 | 说明 |
| :-- | :-- |
| public string OfferId | 【重要】支付应用ID，从米大师获取 |
| public string OpenId |【重要】 用户 OpenID，取值为登录（Login）模块返回的 OpenID |
| public string OpenKey | 用户校验凭证，取值为登录（Login）模块返回的 GuidToken |
| public string SessionId | 米大师会话ID，取值为“hy_gameid” |
| public string SessionType | 米大师会话类型，取值为“st_overseas”（校验登录态）、“st_dummy”（不校验登录态）中的一种 |
| public string Pf | 米大师支付流水，可以通过GetPF方法获取 |
| public string PfKey | 使用iMSDK支付时，取值为“pfKey” |
| public string Country | 国家编码，如：“CN”、“HK”、“US”等 |
| public string CurrencyType | 货币类型简称，如： “CNY”（人民币）、“HKD”（港币）、“USD”（美金）等 |
| public string ProductId |【重要】 米大师商品ID，用于标识一件商品，在米大师管理端进行配置获取 |
| public string PayChannel |【重要】 米大师支付渠道，如：os_link、os_zalo等等，可以从具体可以从米大师获取 |
| public string ZoneId | 米大师的大区ID |
| public string Extras | 扩展字段 |
| public string ResId |【Android】购买货币图标文件资源文件ID，需要放在米大师工程目录的 res/drawable-??/. 目录下。如果图片文件名称为 icon.png， 则这里填写“icon” |
| public string BuyGameOrGoodsOrMonth | 【Android】购买物品类型：“game” - 游戏币、“goods” - 道具、“month” - 包月服务 |
| public string UserExtend | 【Android】Zalo登陆态特定字段，Zalo登陆态下是zalo的userid，不是openid。|
| public string Channel | 【Android】Zalo登陆态特定字段.MSDK分配给Zalo登陆态的编号。|
| public string SaveValue | 【iOS】【可选】充值数量，如：1块钱购买10个钻石，这里填10 |
| public string SaveAmount | 【iOS】充值金额，如：1块钱购买10个钻石，这里填1 |
| public string ProductType | 【iOS】米大师商品类型：0.消费类产品（如钻石） 1.非消费类产品 2.包月+自动续费 3.免费 4.包月+非自动续费 |
| public string IsCanChange | 【iOS】定额是否可改 |
| public string UserId | 【iOS】原始渠道用户ID |
| public string AcctType | 【iOS】【可选】账户类型 |
| public string ProvideUin | 【iOS】他人的QQ号码|
| public string ProvideType | 【iOS】发货类型，跟登录的userId相关，如userId是QQ号，则provideType="uin"；userId是openid的形式，则provideType="openid"|
| public string Extend | 【iOS】扩展字段 |
| public string BizType | 【iOS】 支付类型，用与获取营销活动，"-1"未知类型，"0"游戏币，"1"道具，"4"包月服务，"5"订阅 |
| public string ReqType | 【iOS】请求类型,获取营销活动:ReqType = “mp” |
| public string ServiceCode | 【iOS】包月业务的服务代码|

* 获取商品信息结构体【only for android google pay】 <font color=blue>IMPayMidasProductContent</font>

| 变量 | 说明 |
| :-- | :-- |
| public string ProductId | 米大师商品ID，用于标识一件商品，在米大师管理端进行配置获取 |

####四、支付结果类参考
* 一般支付结果结构体 <font color=blue>IMPayMidasResult</font>

| 类型 | 说明 |
| :-- | :-- |
| public int RetCode | 登录状态码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public int InnerCode | |
| public int RetBillNo | |
| public int RealSaveNum | |
| public int PayChannel |支付渠道，只有支付成功时才返回相应的支付渠道<br>PAYCHANEL_UNKOWN       = -1;</br><br>PAYCHANEL_GOOGLE_WALLET    = 100;</br><br>PAYCHANEL_BOKU   = 101;</br><br>PAYCHANEL_MOL_PIN  = 102;</br><br>PAYCHANEL_MOL_EASYPAY    = 103;</br><br>PAYCHANEL_MOL_WALLET       = 104;</br><br>PAYCHANEL_PAYMENTWALL        = 105;</br><br>PAYCHANEL_MYCARD           = 106;</br><br>PAYCHANEL_ZALO             =107; </br>|
| public int PayState |支付状态,<br>PAYSTATE_PAYUNKOWN     = -1;</br><br>//支付成功</br><br>PAYSTATE_PAYSUCC       = 0;</br><br>//用户取消</br><br>PAYSTATE_PAYCANCEL     = 1;</br><br>//支付出错</br><br>PAYSTATE_PAYERROR      = 2;</br> |
| public int ProvideState |发货状态：<br>PAYPROVIDESTATE_UNKOWN = -1//发货异常，无法知道是否发货成功；</br><br>PAYPROVIDESTATE_SUCC = 0//发货成功 </br>|
| public string ExtendInfo | |     
| public string RespString | 获取商品与营销活动列表信息，Json格式| 
| public string PayReserve1 |-|
| public string PayReserve2 |- |
| public string PayReserve3 | - |    

* 拉取商品或营销活动列表结果<font color=blue>IMPayMidasProductResult</font>   

| 类型 | 说明 |
| :-- | :-- |    
| public int RetCode | 登录状态码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |     
|public List &lt; IMPayMidasResult &gt; productList|商品列表|

* Prepare时返回Google兑换码结果    

| 类型 | 说明 |
| :-- | :-- |    
| public int RetCode | 登录状态码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |     
|public string infor|结果信息|

####五、支付接口参考     
* 支付回调 <font color=blue>PayCallback</font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void MidasPayCallback(IMPayMidasResult result) | 支付结果回调，返回支付结果结构体 |     
|public delegate void MidasProductCallback(IMPayMidasProductResult result)|获取商品或营销活动列表结果回调|    
|public delegate void MidasPayUpdateCallbalk(IMPayMidasUpdateRresult)| 【Android】prepare时从google后台获取兑换码|

* 支付接口说明

|序号 | 方法名 | 方法说明 |        
| :-- | :-- | :-- |        
| 1.|public bool Initialize(List &lt; string &gt; payChannels, string googlePublicKey = "")|【Android】 初始化|   
| 2.|public bool SetChannel(string channel) | 设置支付渠道 |
| 3.|public string GetChannel() | 获取支付渠道 |
| 4.|public void Pay(IMPayMidasContent content, MidasPayCallback callback=null) | 支付 |
| 5.|public void Prepare(IMPayMidasPrepareContent content) | 支付预处理 |
| 6.|public void Prepare(IMPayMidasPrepareContent content, MidasPayUpdateCallback callback) |  <font color=red>【Android特有】支付预处理，该接口增加返回Google兑换码功能 </font>|
| 7.|public void GetProducts(IMPayMidasContent content, MidasProductCallback callback=null)   | 获取商品信息，从midas后台获取，返回信息列表在 `RespString` 参考 `IMPayMidasProductResult` , `IMPayMidasResult` |
| 8.|public void GetProducts(List &lt; IMPayMidasProductContent &gt; productList, MidasProductCallback callback=null)  | <font color=red>【Android特有】获取商品信息，从Google后台获取,返回信息列表在 `RespString` 参考 `IMPayMidasProductResult` , `IMPayMidasResult`</font> |    
| 9.|public bool SetEnv(string env) | 设置支付环境 |
| 10.|public bool EnableDebugLog(bool enable) | 打开Midas调试日志 |
| 11.|public void SetIDC(string idc="hk") | <font color=red>【Android特有】， 新版米大师Google钱包支付设定IDC，需要根据游戏上线位置选择合适的IDC，iOS的IDC设置参考`IMPayMidasPrepareContent` 成员 `Local` </font> |
| 12.|public bool SetScreenType(bool isLandscaple) | <font color=red>【Android特有】， 设置支付屏幕方向，true则为横屏，否则为竖屏</font> |     
>SetIDC方法只支持Android平台，iOS的IDC的设置是在`IMPayMidasPrepareContent`类的成员`Local`来标识


