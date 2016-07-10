## 4.4.13.1 iMSDK功能扩展(Tool)


### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMTool |iMSDK 的扩展工具|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMLogin（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门

1. 代码实例

```cs
	private IMToolDeviceInfo deviceInfoObj;
	private string deviceInfoStr;
    private string public string packageChannelId;
    
    
    deviceInfoObj = IMSDKApi.Tool.GetInfoObj();
    deviceInfoStr = IMSDKApi.Tool.GetInfoStr();
    packageChannelId = deviceInfoObj.PackageChannelId;
    //或者
    //packageChannelId = IMSDKApi.Tool.GetPackageChannelId();

```

### 参考

* GetInfoObj返回结构体 <font color=blue>IMToolDeviceInfo </font>

| 变量 | 说明 |
| :-- | :-- |
| public string PackageChannelId  | 打包渠道ID |
| public string GuestId | 用户GuestID |
| public string AppVersionName | app的versionName |
| public int AppVersionCode | app的versionCode |
| public string OSName | 设备的系统名称 |
| public string OSVersion | 设备系统版本号 | 
| public int Width | 设备宽 |
| public int Height | 设备高 |
| public string Network | 获取设备网络类型，如"tencent-staffwifi" |
| public string IMEI | 设备imei号 |
| public string Operators | 设备运营商 |
| public string Apn | 设备网络apn，如"wap", "net"等 |
| public string Brand | 设备brand |
| public string Manufacturer | 设备制造商 |
| public string Model | 设备model |
| public string PhoneName | 设备名称 |
| public string Language | 设备语言 |
| public string Country | 设备所在国家 |
| public string AndroidId | 设备AndroidId |
| public string Mac |设备mac地址 |
| public string SeriesId | 设备SeriesId |

* 接口说明

| 函数名 | 函数说明 |
| :-- | :-- |
| GetInfoStr() | 获取所有信息，包括如下这些信息(返回 json 字符串) |
| GetInfoObj() | 获取所有信息，包括如下信息(返回 IMToolDeviceInfo ) | 
| GetPackageChannelId() | 获取渠道包apk的packageChannelId |
| GetGuestId() | 获取用户guestId，guestId为用户imsdk用户游客id |
| GetAppVersionName() | 获取应用的versionName |
| GetAppVersionCode() | 获取应用的versionCode |
| GetOSName() | 获取用户操作系统类型，Android用户为"Android" |
| GetOSVersion() | 获取用户操作系统版本，如4.4.4 |
| GetWidth() | 获取设备屏幕宽度 |
| GetHeight() | 获取设备屏幕高度 |
| GetNetwork() | 获取设备网络类型，如"tencent-staffwifi" |
| GetIMEI() | 获取设备imei号 |
| GetOperators() | 获取设备运营商 |
| GetApn() | 获取设备网络apn，如"wap", "net"等 |
| GetBrand() | 获取设备brand |
| GetManufacturer() | 获取设备制造商 |
| GetModel() | 获取设备model |
| GetPhoneName() | 获取设备名称 | 
| GetLanguage() | 获取设备语言 |
| GetCountry() | 获取设备所在国家 |
| GetAndroidId() | 获取设备AndroidId |
| GetMac() | 获取设备mac地址 |
| GetSeriesId() | 获取设备SeriesId |

### 代码示例


```
IMToolDeviceInfo deviceInfoObj = IMSDKApi.Tool.GetInfoObj();
```
```
string deviceInfoStr = 
```

if (GUI.Button (new Rect (0, height, itemWidth/2, itemHeight), "GetInfoStr")) {
			deviceInfoStr = IMSDKApi.Tool.GetInfoStr();
			testInfoAll = deviceInfoStr;
		}
		if (GUI.Button (new Rect (itemWidth/2, height, itemWidth/2, itemHeight), "GetInfoObj")) {
			deviceInfoObj = IMSDKApi.Tool.GetInfoObj();
			testInfoAll = " packageChannelId : " + deviceInfoObj.PackageChannelId
				+ "\n " + "guestId : " + deviceInfoObj.GuestId
					+ "\n " + "appVersionName : " + deviceInfoObj.AppVersionCode
					+ "\n " + "appVersionCode : " + deviceInfoObj.AppVersionCode
					+ "\n " + "osName : " + deviceInfoObj.OSName
					+ "\n " + "osVersion : " + deviceInfoObj.OSVersion
					+ "\n " + "width : " + deviceInfoObj.Width
					+ "\n " + "height : " + deviceInfoObj.Height
					+ "\n " + "network : " + deviceInfoObj.Network
					+ "\n " + "imei : " + deviceInfoObj.IMEI
					+ "\n " + "operators : " + deviceInfoObj.Operators
					+ "\n " + "apn : " + deviceInfoObj.Apn
					+ "\n " + "brand : " + deviceInfoObj.Brand
					+ "\n " + "manufacturer : " + deviceInfoObj.Manufacturer
					+ "\n " + "model : " + deviceInfoObj.Model
					+ "\n " + "phoneName : " + deviceInfoObj.PhoneName
					+ "\n " + "language : " + deviceInfoObj.Language
					+ "\n " + "country : " + deviceInfoObj.Country
					+ "\n " + "androidId : " + deviceInfoObj.AndroidId
					+ "\n " + "mac : " + deviceInfoObj.Mac
					+ "\n " + "seriesId : " + deviceInfoObj.SeriesId;
		}

		height += heightStep;
		if(GUI.Button(new Rect(0,height,itemWidth/2, itemHeight), "PackageChannelId")){
			packageChannelId = IMSDKApi.Tool.GetPackageChannelId();
			testInfo = "packageChannelId is : " + packageChannelId;
		}
		if(GUI.Button (new Rect(itemWidth/2, height, itemWidth/2, itemHeight), "GuestId")){
			guestId = IMSDKApi.Tool.GetGuestId();
			testInfo = "guestId is : " + guestId;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "AppVersionName")){
			appVersionName = IMSDKApi.Tool.GetAppVersionName();
			testInfo = "appVersionName is : " + appVersionName;
		}
		if(GUI.Button(new Rect(itemWidth/3, height, itemWidth/3, itemHeight), "AppVersionCode")){
			appVersionCode = IMSDKApi.Tool.GetAppVersionCode();
			testInfo = "appVersionCode is : " + appVersionCode;
		}
		if (GUI.Button (new Rect (2 * itemWidth / 3, height, itemWidth / 3, itemHeight), "OSName")) {
			osName = IMSDKApi.Tool.GetOSName();
			testInfo = "osName is : " + osName;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "OSVersion")){
			osVersion = IMSDKApi.Tool.GetOSVersion();
			testInfo = "osVersion is : " + osVersion;
		}
		if(GUI.Button(new Rect(itemWidth/3, height, itemWidth/3, itemHeight), "Width")){
			width = IMSDKApi.Tool.GetWidth();
			testInfo = "width is : " + width;
		}
		if (GUI.Button (new Rect (2 * itemWidth / 3, height, itemWidth / 3, itemHeight), "Height")) {
			height = IMSDKApi.Tool.GetHeight();
			testInfo = "height is : " + height;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "Network")){
			network = IMSDKApi.Tool.GetNetwork();
			testInfo = "network is : " + network;
		}
		if(GUI.Button(new Rect(itemWidth/3, height, itemWidth/3, itemHeight), "IMEI")){
			imei = IMSDKApi.Tool.GetIMEI();
			testInfo = "imei is : " + imei;
		}
		if (GUI.Button (new Rect (2 * itemWidth / 3, height, itemWidth / 3, itemHeight), "Operators")) {
			operators = IMSDKApi.Tool.GetOperators();
			testInfo = "operators is : " + operators;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "Apn")){
			apn = IMSDKApi.Tool.GetApn();
			testInfo = "apn is : " + apn;
		}
		if(GUI.Button(new Rect(itemWidth/3, height, itemWidth/3, itemHeight), "Brand")){
			brand = IMSDKApi.Tool.GetBrand();
			testInfo = "brand is : " + brand;
		}
		if (GUI.Button (new Rect (2 * itemWidth / 3, height, itemWidth / 3, itemHeight), "Manufacturer")) {
			manufacturer = IMSDKApi.Tool.GetManufacturer();
			testInfo = "manufacturer is : " + manufacturer;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "Model")){
			model = IMSDKApi.Tool.GetModel();
			testInfo = "model is : " + model;
		}
		if(GUI.Button(new Rect(itemWidth/3, height, itemWidth/3, itemHeight), "PhoneName")){
			phoneName = IMSDKApi.Tool.GetPhoneName();
			testInfo = "phoneName is : " + phoneName;
		}
		if (GUI.Button (new Rect (2 * itemWidth / 3, height, itemWidth / 3, itemHeight), "Language")) {
			language = IMSDKApi.Tool.GetLanguage();
			testInfo = "language is : " + language;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "Country")){
			country = IMSDKApi.Tool.GetCountry();
			testInfo = "country is : " + country;
		}
		if(GUI.Button(new Rect(itemWidth/3, height, itemWidth/3, itemHeight), "AndroidId")){
			androidId = IMSDKApi.Tool.GetAndroidId();
			testInfo = "androidId is : " + androidId;
		}
		if (GUI.Button (new Rect (2 * itemWidth / 3, height, itemWidth / 3, itemHeight), "Mac")) {
			mac = IMSDKApi.Tool.GetMac();
			testInfo = "mac is : " + mac;
		}
		height += heightStep;
		if(GUI.Button(new Rect(0, height, itemWidth/3, itemHeight), "SeriesId")){
			seriesId = IMSDKApi.Tool.GetSeriesId();
			testInfo = "seriesId is : " + seriesId;
		}








