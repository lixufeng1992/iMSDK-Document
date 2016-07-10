### 4.4.5.1 米大师支付


#### * 初始化：设置支付环境、支付预处理
```cs
    IMSDKApi.Pay.Initialize("");//模块功能初始化
    IMSDKApi.Pay.SetChannel("MidasGoogle");//设置渠道
    IMSDKApi.Pay.SetEnv("test");//设置沙箱环境
    IMSDKApi.Pay.EnableDebugLog(true);//设置开启日志
    IMSDKApi.Pay.SetIDC("local");//设置IDC

    /*
    *构造IMPayPrepareContent结构体
    */    
    IMPayPrepareContent prepareContent = new IMPayPrepareContent();
    prepareContent.AppId = "1450005285";
    prepareContent.OpenId = openId;
    prepareContent.OpenKey = accessToken;
    prepareContent.SessionId = "hy_gameid"; // usually "hy_gameid"
    prepareContent.SessionType = "st_overseas"; // check imsdk login status
    prepareContent.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
    prepareContent.PfKey = "pfKey";
    prepareContent.ZoneId = "1";

    IMSDKApi.Pay.Prepare(prepareContent);//支付预处理
```
#### * 基础功能:支付
```cs
    /*
    *构造Pay请求结构体
    */
    IMMidasPayContent GetMidasPayContent() {
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
          content.payChannel = "all";//支付渠道,设置为"all"则支持所有支付渠道，即打开midas商城页
          return content;
        }
    IMSDKApi.Pay.Pay(GetMidasPayContent(),MidasPayCallback);//支付
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
