## 4.4.5.1 米大师支付

#### 基本支付

iMSDK基本支付大致包括：初始化、设置支付环境、支付预处理、最终支付四个流程。
```cs

IMSDKApi.Pay.Initialize("");//模块功能初始化

IMSDKApi.Pay.SetChannel("MidasGoogle");//设置渠道

IMSDKApi.Pay.SetEnv("test");//设置沙箱环境

IMSDKApi.Pay.EnableDebugLog(true);//设置开启日志

IMSDKApi.Pay.SetIDC("local");//设置IDC

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
    
/*
*构造IMPayPrepareContent结构体
*/    
IMPayPrepareContent prepareContent = new IMPayPrepareContent();
prepareContent.AppId = GetMidasPayContent().OfferId;
prepareContent.OpenId = GetMidasPayContent().OpenId;
prepareContent.OpenKey = GetMidasPayContent().OpenKey;
prepareContent.SessionId = GetMidasPayContent().SessionId;
prepareContent.SessionType = GetMidasPayContent().SessionType;
prepareContent.Pf = GetMidasPayContent().Pf;
prepareContent.PfKey = GetMidasPayContent().PfKey;
prepareContent.ZoneId = GetMidasPayContent().ZoneId;

IMSDKApi.Pay.Prepare(prepareContent);//支付预处理
IMSDKApi.Pay.Pay(GetMidasPayContent(),MidasPayCallback);//支付
```


