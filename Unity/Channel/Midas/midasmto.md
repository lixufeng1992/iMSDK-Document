### MidasMTO 工程配置

### MidasMTO配置
* 参考MTO login配置
* 

### MidasMTO代码实例
```
    测试帐号
    testinapppay@gmail.com   271828@!!
```
  
```cs
     content.payChannel = "os_vng";
```

```cs
    /*        
    *Android-Midas 初始化
    */
    IMSDKApi.Pay.Initialize(androidGooglePublicKey);

    IMSDKApi.Pay.SetChannel("MidasMTO");
    IMSDKApi.Pay.SetEnv("dev");//目前暂时只支持dev环境
    IMSDKApi.Pay.EnableDebugLog(true);
    IMSDKApi.Pay.SetIDC("local");

    /*
    *构造Android：IMMidasPayContent
    */
    IMMidasPayContent GetMidasAndroidPayContent() {
     IMMidasPayContent content = new IMMidasPayContent ();
     content.OfferId = "1450007518";
     content.OpenId = "midasoversea";
     content.OpenKey = "midasoversea";
     content.SessionId = "hy_gameid"; // usually "hy_gameid"
     //content.SessionType = "st_overseas"; // check imsdk login status
     content.SessionType = "st_dummy"; // do NOT check imsdk login status
     content.ZoneId = "1";
     content.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
     content.PfKey = "pfKey";
     content.ProductId = "com.vng.wmb.item20";
     content.ResId = "unipay_abroad_iconload";
     content.Country = "US";
     content.CurrencyType = "USD";
     content.BuyGameOrGoodsOrMonth = "Game";//Game:钻石 Goods:道具 Month:月卡
     content.payChannel = "os_vng";
     return content;
     }

    /*
    *构造iOS：IMMidasPayContent
    *请注意在构造Android和iOS时的细微差别
    */
    IMMidasPayContent GetMidasIOSPayContent() {
     IMMidasPayContent content = new IMMidasPayContent ();
     
     return content;
     }

    /*
     *构造IMPayPrepareContent
    */
    IMPayPrepareContent prepareContent = new IMPayPrepareContent();
    prepareContent.AppId = GetMidasAndroidPayContent().OfferId;
    prepareContent.OpenId = GetMidasAndroidPayContent().OpenId;
    prepareContent.OpenKey = GetMidasAndroidPayContent().OpenKey;
    prepareContent.SessionId = GetMidasAndroidPayContent().SessionId;
    prepareContent.SessionType = GetMidasAndroidPayContent().SessionType;
    prepareContent.Pf = GetMidasAndroidPayContent().Pf;
    prepareContent.PfKey = GetMidasAndroidPayContent().PfKey;
    prepareContent.ZoneId = GetMidasAndroidPayContent().ZoneId;

    IMSDKApi.Pay.Prepare(prepareContent);


    /*
    *Pay:支付
    */
    IMSDKApi.Pay.Pay(GetMidasAndroidPayContent(),MidasPayCallback);

```
