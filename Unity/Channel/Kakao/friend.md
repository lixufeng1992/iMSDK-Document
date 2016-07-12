# Kakao 好友功能说明


## 关系链功能支持列表

| 序号 | 功能 | 是否支持 | 备注 |
| :--: | :--: | :----: | :--: |
| 1 | 邀请 |  √ | - |
| 2 | 发送文本-后台 | √ | - |
| 3 | 发送文本-对话框 | x | - |
| 4 | 发送链接-后台 | x | - |
| 5 | 发送链接-对话框 | x | - |
| 6 | 发送图片-后台 | √ | - |
| 7 | 发送图片-对话框 | x | - |


## 字段填写规则

| 分享类型 | 用户ID | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson）|
| :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| 邀请 | √（用户UUID） | x | x | x | x | - | √ |
| 发送文本（后台） | √（用户UUID） | x | x | x | x | x | √ |
| 发送图片（后台） | √（用户UUID）| x | x | x | √ | x | √ |

扩展字段（ExtraJson）传参说明
> 扩展字段的传参依赖于后台的配置，此
* 邀请：
  * 邀请好友加入游戏。发送消息钱先调用flkkextend模块或kakaoextend模块的getInvitableFriends（）获取未绑定游戏的好友列表
  ```code
  // convert dictionary to json string
  // content.ExtraJson = "{\"templateId\":\"254\",\"${sender_name}\":\"sender_test\"}";
  Dictionary<string, string> extra = new Dictionary<string, string>();
  extra.Add("templateId", "254");
  extra.Add("${sender_name}","sender_test");
  content.ExtraJson = Json.Serialize(extra);
  ```
* 发送文本：
  * 给好友发送文字消息。发送消息前现调用flkkextend或kakaoextend模块的getRegisteredFriends（）获取绑定游戏的好友列表
  ```code
  // convert dictionary to json string
  // content.ExtraJson =  "{\"templateId\":\"271\",\"${sender_name}\":\"sender_test\",\"${image_url}\":\"https://www.baidu.com/img/bdlogo.png\"}"；
  Dictionary<string, string> extra = new Dictionary<string, string>();
  extra.Add("templateId", "271");
  extra.Add("${sender_name}","sender_test");
  extra.Add("${image_url}","https://www.baidu.com/img/bdlogo.png");
  content.ExtraJson = Json.Serialize(extra);
  ```
* 发送图片：
  * 给好友发送图片消息。发送消息前现调用flkkextend模块或kakaoextend模块的getRegisteredFriends（）获取绑定游戏的好友列表
  ```code
    // convert dictionary to json string
    // content.ExtraJson = "{\"templateId\":\"274\",\"${sender_name}\":\"sender_test\"}";
    Dictionary<string, string> extra = new Dictionary<string, string>();
    extra.Add("templateId", "274");
    extra.Add("${sender_name}","sender_test");
    content.ExtraJson = Json.Serialize(extra);
  ```

## 工程配置

### Android工程配置

* 参考配置：
* 
``` xml
<manifest 
      package="com.tencent.imsdk.kakao.friend"
      xmlns:android="http://schemas.android.com/apk/res/android"> 
      <uses-permission android:name="android.permission.INTERNET"/> 
      <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/
      <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/> 
      <uses-sdk android:minSdkVersion="10"/> 
      <!--you need inherit Application class and add initialize function in your application class-->
      <application android:name="com.tencent.imsdk.unity.kakao.GlobalApplication"> 
      <!--you should replace or copy inner config to your man activity-->
       <activity android:name=".{your main activity}"> 
           <intent-filter> 
               <action android:name="android.intent.action.VIEW"/> 
               <category android:name="android.intent.category.DEFAULT"/> 
               <category android:name="android.intent.category.BROWSABLE"/> 
               <data android:scheme="kakao{your kakao native app key}"/> 
           </intent-filter> 
           <intent-filter> 
               <action android:name="android.intent.action.VIEW"/> 
               <category android:name="android.intent.category.DEFAULT"/> 
               <category android:name="android.intent.category.BROWSABLE"/> 
               <data android:scheme="kakao{your kakao native app key}"
                     android:host="kakaolink"/> 
           </intent-filter> 
           <intent-filter> 
               <action android:name="android.intent.action.VIEW"/> 
               <category android:name="android.intent.category.DEFAULT"/> 
               <category android:name="android.intent.category.BROWSABLE"/> 
               <data android:scheme="kakao{your kakao native app key}"
               android:host="kakaostory"/> 
           </intent-filter> 
       </activity> 
       <meta-data 
           android:name="com.kakao.sdk.AppKey" 
           android:value="{your kakao native app key}"/> 
      </application> 
  </manifest>
 ```


  
### iOS工程配置

按Facebook工程通用配置进行配置即可

