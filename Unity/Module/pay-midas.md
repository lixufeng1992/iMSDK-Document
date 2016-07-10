### 4.4.5.1 米大师支付

####快速入门
1. [完成特定渠道配置](../../Channel/midas.md)   
2. 代码实例

```cs
    /*
    *构造支付预处理结构体：IMPayPrepareContent
    */  
    IMPayPrepareContent CreatePrepareContent(){
      IMPayPrepareContent prepareContent = new IMPayPrepareContent();
      prepareContent.AppId = "1450005285";
      prepareContent.OpenId = openId;
      prepareContent.OpenKey = accessToken;
      prepareContent.SessionId = "hy_gameid"; // usually "hy_gameid"
      prepareContent.SessionType = "st_overseas"; // check imsdk login status
      prepareContent.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
      prepareContent.PfKey = "pfKey";
      prepareContent.ZoneId = "1";
  }
   
   /*
    *构造支付结构体：IMMidasPayContent
    */ 
   IMMidasPayContent GetMidasPayContent(){
          IMMidasPayContent content = new IMMidasPayContent ();
          content.OfferId = "1450005285";
          content.OpenId = openId;
          content.OpenKey = accessToken;
          content.SessionId = "hy_gameid"; // usually "hy_gameid"
          //content.SessionType = "st_overseas"; // check imsdk login status
          content.SessionType = "st_dummy"; // do NOT check imsdk login status
          content.ZoneId = "1";
          content.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
          content.PfKey = "pfKey";
          content.ProductId = "midas_product_1";
          content.ResId = "unipay_abroad_iconload";
          content.Country = "US";
          content.CurrencyType = "USD";
          content.BuyGameOrGoodsOrMonth = "Goods";//Game:钻石 Goods:道具 Month:月卡
          //支付渠道,设置为"all"则支持所有支付渠道，即打开midas商城页
          content.payChannel = "all";
          return content;
   }
   
    /*
    *初始化：设置支付环境、支付预处理等
    */
    void Start() {
        IMSDKApi.Pay.Initialize("");//模块功能初始化
        IMSDKApi.Pay.SetChannel("MidasGoogle");//设置渠道
        IMSDKApi.Pay.SetEnv("test");//设置沙箱环境
        IMSDKApi.Pay.EnableDebugLog(true);//设置开启日志
        IMSDKApi.Pay.SetIDC("local");//设置IDC
        IMSDKApi.Pay.Prepare(CreatePrepareContent());//支付预处理
    }
    
    /*
    *支付
    */
    void TestPay(){
        IMSDKApi.Pay.Pay(GetMidasPayContent(),MidasPayCallback);//支付
    }
```

####进阶功能：获取谷歌兑换码、获取营销活动、获取商品信息
1. 代码实例   
 
```cs
   void Start() {
        //见快速入门 初始化：设置支付环境、支付预处理等
    }
    
    /*
    *prepare：支付预处理2,Android特有,增加支持返回google兑换码功能
    */
    void TestPrepareForGoogle(){
       IMSDKApi.Pay.Prepare(prepareContent,MidasPayUpdateCallback);
    }
    
    /*
    *GetMP:获取营销活动
    */
    void TestGetMP(){
       IMSDKApi.Pay.GetMP(GetMidasAndroidPayContent(), MidasPayCallback);
    }
    
   /*
    *GetProducts:获取商品信息(从Midas后台获取)
    */
    void TestGetProducts(){
       List<IMMidasPayContent> list = new List<IMMidasPayContent>();
       list.Add(GetMidasAndroidPayContent());
       IMSDKApi.Pay.GetProducts(list, MidasProdctCallback);
    }
    
    /*
    *GetProducts:获取商品信息2(从Google后台获取),只适用于Android平台
    */
    void TestGetProductsFromGoogleSRV(){
       List<IMMidasProductContent> list = new List<IMMidasProductContent>();
       list.Add("your_google_productId1");
       list.Add("your_google_productId2");
       ...
      IMSDKApi.Pay.GetProducts(list, MidasProdctCallback);
    }
    
```
#### 支付流程说明

* 米大师支付分为初始化（Initialize）、设置支付渠道（SetChannel）、设置支付环境（SetEnv）、设置支付区域（SetIDC）、支付准备（Prepare）、支付（Pay）这几个步骤

  1. 初始化，在支付流程中，必须先调用出售化接口才能调用其他函数，包括支付和设置支付渠道
  
    ```cs
    IMSDKApi.Pay.Initailize( YOUR_GOOGLE_PUBLIC_KEY );
    ```
		
	设置支付渠道，米大师支付流程中，支付渠道都是“Midas”开头的字符串

    ```cs
    IMSDKApi.Pay.SetChannel( YOUR_PAY_CHANNEL );
    ```
  2. 【可选】打开支付日志，测试时建议打开日志，便于定位问题，测试完成后可以关闭

    ```cs
    IMSDKApi.Pay.EnableDebugLog( YOUR_CHOICE );
    ```

  3. 设置支付环境，支付环境一般为测试（“test”）或者正式环境（“release”）

    ```cs
    IMSDKApi.Pay.SetEnv( YOUR_PAY_ENVIRONMENT ); 
    ```
    
  4. 设置支付服务器区域，一般根据自己游戏需要，选择合适的支付区域

    ```cs
    IMSDKApi.Pay.SetIDC( YOUR_PAY_AREA );
    ```
    
  5. 支付准备，该步骤一般在登录操作完成后进行

    ```cs
    IMSDKApi.Pay.Prepare( YOUR_PREPARE_CONTENT );
    ```
    
  6. 支付，只有完成上述步骤后，才能调用支付方法
    
    ```cs
    IMSDKApi.Pay.Pay( YOUR_PAY_CONTENT, YOUR_PAY_CALLBACK );
    ```
    
* 获取商品列表，包括两种方式：从米大师获取商品列表信息；从支付平台获取商品列表信息
  
  ```cs
  IMSDKApi.Pay.GetProducts( YOUR_PRODUCT_LIST, YOUR_PRODUCT_CALLBACK );
  ```		
  返回信息为JSON字符串，需要游戏自行解析
	
* 获取营销活动信息

  ```cs
  IMSDKApi.Pay.GetMP( YOUR_PAY_CONTENT, YOUR_MP_CALLBACK );
  ```
  
  
 #### 参考

* 支付准备信息结构体 <font color=blue>IMPayPrepareContent</font>

| 变量 | 说明 |
| :-- | :-- |
| public string AppId | 支付应用ID，又称为OfferId，从米大师获取 |
| public string OpenId | 用户 OpenID，取值为登录（Login）模块返回的 OpenID |
| public string OpenKey | 用户校验凭证，取值为登录（Login）模块返回的 GuidToken |
| public string SessionId | 米大师会话ID，取值为“hy_gameid” |
| public string SessionType | 米大师会话类型，取值为“st_overseas”（校验登录态）、“st_dummy”（不校验登录态）中的一种 |
| public string Pf | 米大师支付流水，可以通过GetPF方法获取 |
| public string PfKey | 使用iMSDK支付时，取值为“pfKey” |
| public string ZoneId | 米大师的大区ID，该ID需要在米大师管理端进行配置 |
| public string Env <sup> * </sup> | 【iOS】【可选】米大师支付环境，取值为“test”（测试）、“release”（正式）中的一种 |
| public string Local <sup> * </sup> | 【iOS】【可选】米大师支付区域，该值需要根据游戏的发布地区确认，如：“hongkong”（香港） |
| public string SessionChannel <sup> * </sup> | 【iOS】登录渠道，与登录模块中的渠道ID定义保持一致，如：1（Facebook）、2（GameCenter）、3（Google Play & Plus）、4（Wechat）、5（iMSDK Guest）等等 |

<font color=green><sup> * </sup>说明：Env和Local为iOS专有字段，如果iOS环境下已经调用了SetEnv和SetIDC方法，这两个字段可以不填</font>


* 支付信息结构体 <font color=blue>IMMidasPayContent</font>

| 变量 | 说明 |
| :-- | :-- |
| public string OfferId | 支付应用ID，又称为AppId，从米大师获取 |
| public string OpenId | 用户 OpenID，取值为登录（Login）模块返回的 OpenID |
| public string OpenKey | 用户校验凭证，取值为登录（Login）模块返回的 GuidToken |
| public string SessionId | 米大师会话ID，取值为“hy_gameid” |
| public string SessionType | 米大师会话类型，取值为“st_overseas”（校验登录态）、“st_dummy”（不校验登录态）中的一种 |
| public string Pf | 米大师支付流水，可以通过GetPF方法获取 |
| public string PfKey | 使用iMSDK支付时，取值为“pfKey” |
| public string Country | 国家编码，如：“CN”、“HK”、“US”等 |
| public string CurrencyType | 货币类型简称，如： “CNY”（人民币）、“HKD”（港币）、“USD”（美金）等 |
| public string ProductId | 米大师商品ID，用于标识一件商品，在米大师管理端进行配置获取 |
| public string PayChannel | 米大师支付渠道，如：os_link、os_zalo等等，可以从具体可以从米大师获取 |
| public string ZoneId | 米大师的大区ID |
| public string Extras | 扩展字段 |
| public string ResId |【Android】购买货币图标文件资源文件ID，需要放在米大师工程目录的 res/drawable-??/. 目录下。如果图片文件名称为 icon.png， 则这里填写“icon” |
| public string BuyGameOrGoodsOrMonth | 【Android】购买物品类型：“game” - 游戏币、“goods” - 道具、“month” - 包月服务 |
| public string UserExtend | 【Android】|
| public string Channel | 【Android】|
| public string SaveValue | 【iOS】【可选】充值数量，如：1块钱购买10个钻石，这里填10 |
| public string SaveAmount | 【iOS】充值金额，如：1块钱购买10个钻石，这里填1 |
| public string ProductType | 【iOS】米大师商品类型：0.消费类产品（如钻石） 1.非消费类产品 2.包月+自动续费 3.免费 4.包月+非自动续费 |
| public string IsCanChange | 【iOS】 |
| public string UserId | 【iOS】原始渠道用户ID |
| public string AcctType | 【iOS】【可选】账户类型 |
| public string ProvideUin | 【iOS】|
| public string ProvideType | 【iOS】|
| public string Extend | 【iOS】扩展字段 |
| public string bizType | 【iOS】 支付类型，用与获取营销活动，"-1"未知类型，"0"游戏币，"1"道具，"4"包月服务，"5"订阅 |
| public string reqType | 【iOS】 |
| public string serviceCode | 【iOS】|

* 获取商品信息结构体 <font color=blue>IMMidasProductContent</font>

| 变量 | 说明 |
| :-- | :-- |
| public string ProductId | 米大师商品ID，用于标识一件商品，在米大师管理端进行配置获取 |

* 一般支付结果结构体 <font color=blue>IMPayResult</font>

| 类型 | 说明 |
| :-- | :-- |
| public int RetCode | 登录状态码，一般 1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public int InnerCode | |
| public int RetBillNo | |
| public int RealSaveNum | |
| public int PayChannel | |
| public int PayState | |
| public int ProvideState | |
| public int ExtendInf | |
| public int ExtendInfo1 | |
| public int ExtendInfo2 | |
| public int ExtendInfo3 | - |


* 支付回调 <font color=blue>PayCallback</font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void PayCallback(IMPayResult result) | 登录回调函数，返回支付结果结构体 |
	
|序号 | 方法名 | 方法说明 |
| :-- | :-- | :-- |
| 1.|public bool Initialize(List< string > payChannels, string googlePublicKey = "")| <font color=red>Android特有，初始化 </font>|
| 2.|public bool Initialize(string googlePublicKey = "") | 同方法1， 默认从IMSDK/pay.json中读取payChannels |
| 3.|public bool SetEnv(string env) | 设置支付环境 |
| 4.|public bool EnableDebugLog(bool enable) | 打开支付调试日志 |
| 5.|public void SetIDC(string idc="hk") | <font color=red>Android特有， 新版米大师Google钱包支付设定IDC，需要根据游戏上线位置选择合适的IDC</font> |
| 6.|public bool SetScreenType(bool isLandscaple) | <font color=red>Android特有， 设置支付屏幕方向，true则为横屏，否则为竖屏</font> |
| 7.|public bool SetChannel(string channel) | 设置支付渠道 |
| 8.|public string GetChannel() | 获取支付渠道 |
| 9.|public void Pay(IMMidasPayContent content, MidasPayCallback callback=null) | 支付，iOS-Midas支付及Android-Midas支付 |
| 10.|public void Pay(IMUJoyPayContent content, UJoyPayCallback callback=null)  | 支付，三七玩接口特有 |
| 11.|public void Prepare(IMPayPrepareContent content) | 支付预处理 |
| 12.|public void Prepare(IMPayPrepareContent content, MidasPayUpdateCallback callback) |  <font color=red>支付预处理，Android特有，该接口增加返回Google兑换码功能 </font>|
| 13.|public void GetMP(IMMidasPayContent content,  MidasPayCallback callback=null) | 获取营销活动 |
| 14.|public void GetProducts(List< IMMidasPayContent > productList, MidasProductCallback callback=null)   | 获取商品信息，从midas后台获取 |
| 15.|public void GetProducts(List< IMMidasProductContent > productList, MidasProductCallback callback=null)  | <font color=red>获取商品信息，Android特有，从Google后台获取</font> |
| 16.|public void GetProducts(IMUJoySkuContent content, UJoyProductCallback callback=null)  | 获取商品信息，三七玩渠道特有 |
| 17.|public void SetRegisterCallback(PayCallback callback) | 设置初始化回调函数 |
| 18.|public void SetOrderCallback(PayCallback callback) | 设置下订单回调函数 |
| 19.|public void SetPurchaseCallback(MidasGooglePayCallback callback) | Android 设定米大师Google支付步骤回调 |
| 20.|public void SetDistributeCallback(PayCallback callback) | 设定发货回调 |
| 21.|public void SetPayCallback(PayCallback callback) | 设定支付回调 |
| 22.|public void SetErrorCallback(PayCallback callback) | 设定其他出错回调 |



##### * 基础功能:支付
```cs
    /*
    *构造Pay请求结构体
    */
    IMMidasPayContent GetMidasPayContent() {
          
          return content;
        }
    
```

#### * 进阶功能：获取营销活动
```cs
    IMSDKApi.Pay.GetMP(GetMidasPayContent(), MidasPayCallback);
```

#### * 进阶功能：获取商品信息(从Midas后台获取)
```cs
    List<IMMidasPayContent> list = new List<IMMidasPayContent>();
    list.Add(GetMidasAndroidPayContent());
    IMSDKApi.Pay.GetProducts(list, MidasProdctCallback);
```
