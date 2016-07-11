## 4.4.13.4 Efun功能扩展


### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Efun |Efun扩展功能|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMEfun（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门
1.代码实例
  ```
			//展示 platform
			EfunPlatformEntity param = new EfunPlatformEntity();
			param.serverCode = "9999";
			param.roleId = "1";
			param.roleLevel = "1";
			param.roleName = "think";
			IMSDKApi.Efun.ShowPlatform(param);
			
			//隐藏 platform
			IMSDKApi.Efun.HiddenPlatform(true);
	
			//关联第三方社交平台
			IMSDKApi.Efun.Relate2ThirdAccount(0,OnRelate2ThirdAccount);
			
			//获取好友
			IMSDKApi.Efun.GetInvitableFriends(0,OnGetFriends);
	
			//获取用户信息
			IMSDKApi.Efun.GetUserProfile(0， 100， 100 ,OnGetUserProfile);
		
		
```


  
###参考

* 
Efun扩展类方法 <font color=blue>IMEfun</font>   

| 函数名 | 函数说明 |
| :-- | :-- |
| public void ShowPlatform(EfunPlatformEntity param)|Platform展示,<br>param说明参考EfunPlatformEntity结构体|
|public void HiddenPlatform(bool isHidePlatform = true)|Platform隐藏，<br>isHidePlatform为true时隐藏，否则不隐藏|
| public void Relate2ThirdAccount(int kind,EfunRelate2ThirAccountCallback callback = null)|关联第三方平台账号，<br>Kind分别为 0：Facebook；1：Kakao；2：VK；3：Twitter|
| public void GetInvitableFriends(int kind,EfunGetFriendCallback callback = null)|获取可邀请好友（**注意与Friend模块好友的区别**），<br>Kind分别为 0：Facebook；1：Kakao；2：VK；3：Twitter|
|public void GetUserProfile(int kind, int width, int height, EfunGetuserProfileCallback callback = null)|获取用户信息。<br>Kind分别为 0：Facebook；1：Kakao；2：VK；3：Twitter。<br>width与height是用户头像的宽高|
  
+ 回调  

|回调函数名|回调说明|  
| -- | -- |  
| public delegate void EfunRelate2ThirAccountCallback(int code)|code:关联结果码：<br>0：表示关联失败；1：关联成功同步成功；2：关联成功同步失败|
|public delegate void EfunGetFriendCallback(EfunFriendResult result)|返回结果参考EfunFriendResult|
|public delegate void EfunGetuserProfileCallback(EfunUserProfile result)|返回结果参考EfunUserProfile|
  

+ 好友结果信息   （EfunFriendResult）

|属性|说明|  
| :-- | :-- |  
| public int retCode|返回码|   
|public string retMsg|返回信息|   
|public int imsdkRetCode|IMSDK返回码|    
|public string imsdkRetMsg|IMSDK返回信息|    
|public int thirdRetCode|第三方返回码|    
|public string thirdRetMsg|第三方返回信息|    
|public string retExtraJson|额外参数|
|public List<EfunFriendProfile> friendList|没有在游戏中的好友，也就是可以邀请的好友|



+ 好友信息 (EfunFriendProfile) 

|属性|说明| 
| -- | -- |  
|public string userName|用户姓名|   
|public string userId|用户ID|   
|public int height|用户头像高|   
|public int width|用户头像宽|    
|public bool isSilhouette|不知道haha|    
|public string imageUrl|用户头像URL|


+ 用户信息（EfunUserProfile）     

|属性|说明| 
| :-- | :-- |  
|public string userName|用户姓名|   
|public string userId|用户ID|   
|public string loginType|登入子渠道|   
|public string gender|用户性别|    
|public bool isSilhouette|不知道haha|    
|public string imageUrl|用户头像URL|

### 代码示例
```
			//show platform
			EfunPlatformEntity param = new EfunPlatformEntity();
			param.serverCode = "9999";
			param.roleId = "1";
			param.roleLevel = "1";
			param.roleName = "think";
			IMSDKApi.Efun.ShowPlatform(param);
			
			//hide platform
			IMSDKApi.Efun.HiddenPlatform(true);
	
			//relate to third account
			IMSDKApi.Efun.Relate2ThirdAccount(0,OnRelate2ThirdAccount);
			
			//get invitable friends
			IMSDKApi.Efun.GetInvitableFriends(0,OnGetFriends);
	
			//get user profile
			IMSDKApi.Efun.GetUserProfile(0， 100， 100 ,OnGetUserProfile);
		
		
```
###配置说明   

#### iOS 配置说明     
 
+ 配置与Login一样

####Android 配置说明
 + 	参考Login，作如下修改
 + 	（1）删除如下权限
		<uses-permission android:name="android.permission.GET_TASKS" />
	
	（2）删除如下配置：
		
        <service android:name="com.efun.push.client.service.EfunPushService" >
        </service>

        <receiver android:name="com.efun.push.client.receiver.EfunPushReceiver" >
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
                <action android:name="com.efun.push.client.Dispatcher" />
                <action android:name="com.efun.delete.notification.action" />
            </intent-filter>
        </receiver>
        

	（3）修改原sdk中所有Activity中的android:screenOrientation属性：
		将android:screenOrientation="landscape" 改为 android:screenOrientation="sensorLandscape"