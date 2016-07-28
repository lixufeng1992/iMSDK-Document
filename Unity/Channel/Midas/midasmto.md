### MidasMTO 工程配置

### MidasMTO配置
* 参考MTO login配置

### MidasEfun代码实例
  
```cs
    /*
     *差别部分：
     *payChannel值为：os_efun时，开启Efun谷歌支付
     *payChannel值为：os_efunwap，开启Efun普通支付
     */
     content.payChannel = "os_efun";

     /*
     *需要游戏拼凑该字符串
     *roleId值
     *roleName值
     *roleLevel值
     *serverId值
     */
     content.Extras = "roleId=aaaa&roleName=bbbb&roleLevel=cccc&serverId=1";
```

```cs
    /*        
    *Android-Midas 初始化
    */
    IMSDKApi.Pay.Initialize(androidGooglePublicKey);

    IMSDKApi.Pay.SetChannel("MidasEfun");
    IMSDKApi.Pay.SetEnv("dev");//目前暂时只支持dev环境
    IMSDKApi.Pay.EnableDebugLog(true);
    IMSDKApi.Pay.SetIDC("local");

    /*
    *构造Android：IMMidasPayContent
    */
    IMMidasPayContent GetMidasAndroidPayContent() {
     IMMidasPayContent content = new IMMidasPayContent ();
     content.OfferId = "1450007160";
     content.OpenId = openId;
     content.OpenKey = accessToken;
     content.SessionId = "hy_gameid"; // usually "hy_gameid"
     //content.SessionType = "st_overseas"; // check imsdk login status
     content.SessionType = "st_dummy"; // do NOT check imsdk login status
     content.ZoneId = "1";
     content.Pf = IMSDKApi.Pay.GetPf (openId, "2001", "2011", "IMSDK");
     content.PfKey = "pfKey";
     content.ProductId = "tw.qmcs.100usd";
     content.ResId = "unipay_abroad_iconload";
     content.Country = "US";
     content.CurrencyType = "USD";
     content.BuyGameOrGoodsOrMonth = "Game";//Game:钻石 Goods:道具 Month:月卡

     /*
         *payChannel值为：os_efun时，开启Efun谷歌支付
         *payChannel值为：os_efunwap，开启Efun普通支付
     */
     content.payChannel = "os_efun";
     content.Extras = "roleId=aaaa&roleName=bbbb&roleLevel=cccc&serverId=1";
     return content;
     }

    /*
    *构造iOS：IMMidasPayContent
    *请注意在构造Android和iOS时的细微差别
    */
    IMMidasPayContent GetMidasIOSPayContent() {
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
     content.Country = "CN";
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

    /*
    *efun暂时不支持 获取营销活动、获取商品信息功能
    */
```
