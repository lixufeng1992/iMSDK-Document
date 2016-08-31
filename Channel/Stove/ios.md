## 6.10.3 Stove(iOS) 工程配置

###将下列framework加入目标工程
+ Bolts.framework
+ FBAudienceNetwork.framework
+ FBSDKCoreKit.framework
+ FBSDKLoginKit.framework
+ FBSDKMessengerShareKit.framework
+ FBSDKShareKit.framework
+ FacebookSDKStrings.bundle
+ GoogleSignIn.bundle
+ GoogleSignIn.framework
+ StoveBundle.bundle
+ StoveSDK.framework
+ IMSDKAppSetting.bundle
+ IMSDKCoreKit.framework
+ IMSDKExtendStove.framework
+ IMSDKLoginStove.framework
+ IMSDKPushStove.framework

###系统库依赖
+ libxml2.2.tbd
+ libz.tbd
+ libsqlite3.0.tbd
+ libresolv.tbd
+ libiconv.tbd
+ CoreLocation.framework
+ CoreTelephony.framework
+ AdSupport.framework
+ Foundation.framework
+ StoreKit.framework
+ AudioToolbox.framework
+ AVFoundation.framework
+ MobileCoreServices.framework
+ AddressBook.framework
+ ImageIO.framework
+ SystemConfiguration.framework
+ CoreData.framework
+ CFNetwork.framework
+ CoreText.framework
+ MediaPlayer.framework
+ CoreMotion.framework

###info.plist文件配置

1. 新增**FacebookAppID**，并填入目标Facebook app id
2. 新增**GooglePlusClientID**配置项，并填入目标Google app id
3.  URL Schemes 添加
  
    + Facebook, fb408057129368811 :  fb + FacebookAppID 
    + Google,  Google+ REVERSED_CLIENT_IDvalue 
    + 添加项目bundleid