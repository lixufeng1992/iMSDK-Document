# Stove扩展(StoveExtend)

## 命名空间

```cs
using Tencent.iMSDK
```

## 接口类

```cs
IMSDKApi.IMStove
```

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMStove（GameObject）上，开发者不要主动销毁该对象！</font>

## 模块使用说明
与iMSDKStove登录模块配合使用

### 基本功能

主要 初始化、展示弹窗、设置推送开关、获取配置信息等

## 工程配置说明

### Android工程配置说明

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

### iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。

## 参考
###iMSDK返回基础结构体
* iMSDK基础结构体【iMSDK不同返回结构体都继承于IMResult】  <font color=blue>IMResult</font>

| 变量 | 说明 |
| :-- | :-- |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg| 错误信息 |
| public int IMSDKRetCode| iMSDK返回码 ，1 为成功，其他为失败  |
| public int IMSDKRetMsg|  iMSDK 返回信息 |
| public int ThirdRetCode| 第三方返回码 |
| public int ThirdRetMsg| 第三方返回信息|
| public int RetExtraJson| 扩展信息 |

* 回调代理函数 <font color=blue>无,IMResult为所有返回结构体基类</font>


###初始化&获取配置信息结构体及回调代理函数
*  初始化&获取配置信息结构体  <font color=blue>IMStoveConfigResult ：IMResult </font>    

*  【注意：初始化 与  获取配置信息 返回的结构体相同】     
   
| 变量 | 说明 | 
| :-- | :-- |
| public string GameIp| 游戏IP地址 |
| public int GamePort| 端口 |

* 回调代理函数 <font color=blue> IMStoveConfigCallback </font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void IMStoveConfigCallback(IMStoveConfigResult result) | 初始化&获取配置信息，返回结构体 |

###展示Banner结构体及回调代理函数
* 展示弹窗结构体 <font color=blue>IMStoveLaunchUIResult ：IMResult </font>

| 变量 | 说明 |
| :-- | :-- |
| public int UiNum| 弹窗类型 |
| public string Portrait| 头像url |
| public string AccessToken| stove token |
| public string MemberId| stove memberId |
| public string NickName| stove nickName |
| public string MemberNo| stove memberNo |
| public string AccountType| stove accountType |

* 回调代理函数 <font color=blue>IMStoveLaunchUICallBack</font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void IMStoveLaunchUICallBack(IMStoveLaunchUIResult result) | 展示弹窗回调函数|

###设置推送开关结构体    

* 展示弹窗结构体 <font color=blue>IMStovePushResult：IMResult </font>

| 变量 | 说明 |
| :-- | :-- |
| public bool IsActive| 推送开启或关闭 |

* 回调代理函数 <font color=blue>IMStovePushBack</font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void IMStovePushBack(IMStovePushResult result) |  设置推送  |

###设置监听LaunchUI中的点击登出、删除游戏角色、退出游戏、删除游戏账号结构体   

* 展示弹窗结构体 <font color=blue>IMStoveLaunchActionResult：IMResult </font>

| 变量 | 说明 |
| :-- | :-- |
| public int Type| 回调类型 |

| Type定义 | 取值 |
| :-- | :-- |
| LAUNCHUI_ACTION_LOGOUT| 2 |
| LAUNCHUI_ACTION_DEL_CHARACTER| 3 |
| LAUNCHUI_ACTION_EXIT_GAME| 7 |
| LAUNCHUI_ACTION_DEL_ACCOUNT| 17 |

* 回调代理函数 <font color=blue>IMStoveLaunchActionCallBack</font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void IMStoveLaunchActionCallBack(IMStoveLaunchActionResult result); |  设置监听LaunchUI中事件回调  |

###设置监听预登陆回调  
* 回调代理函数 <font color=blue>IMStovePrepareLoginCallBack</font>

| 类型 | 说明 |
| :-- | :-- |
| public delegate void IMStovePrepareLoginCallBack(IMResult result); |  设置监听预登录回调  |

* IMStove方法类 <font color=blue> IMStove </font>

| 函数名 | 函数说明 |
| :-- | :-- |
| public void Initialize (IMStoveConfigCallback callback) | 初始化方法，在调用其他函数之前必须调用该函数 |
| public void LaunchUI (int uiType, IMStoveLaunchUICallBack callback, int noticeParam = 0) | 展示弹窗|
| public void getConfigInfo (IMStoveConfigCallback callback) | 获取配置信息 |
| public void SetPushActive (bool isActive, IMStoveCallBack callback) | 设置推送开关 |
| public void GetPushInfo (IMStovePushBack callback) | 获取推送开关 |
| public void PrepareLogin(IMStovePrepareLoginCallBack callback) | 预登录 |
| public void SetLaunchActionCallBack(IMStoveLaunchActionCallBack callback) | 设置监听LaunchUI中的点击登出、删除游戏角色、退出游戏、删除游戏账号回调 |
| public void SetWorldID(string worldID) | 设置大区 |
| public void PermissionCheck(IMStovePermissionCheckCallBack callback) |（仅支持Android）申请、检查权限,建议在初始化完成之后，登录之前调用 |
## 代码示例

```cs
/**
  *Stove初始化为异步方法，调用登录接口前请务必确定已完成初始化
*/
public void PrintResult(IMResult result)
{
    IMLog.Log("print result " + result.IMSDKRetCode);
}

public void PrintInitCallCallback(IMStoveConfigResult result)
{
   //申请权限建议在初始化完成之后，登录之前调用
   TestPermissionCheck();
   
   //建议游戏当申请权限成功后，再调用登录接口
   IMLog.Log("print result " + result.IMSDKRetCode);
}

public void PrintConfigResult(IMStoveConfigResult result)
{
   IMLog.Log("print result " + result.IMSDKRetCode);
}

public void PrintLaunchUIResult(IMStoveLaunchUIResult result)
{
   IMLog.Log("print result " + result.IMSDKRetCode);
}

void Start()
{
   IMLog.setLevel(IMLog.Level.Log);
   IMStove.Instance.Initialize(PrintInitCallCallback);
}

void Test()
{
    //展示弹窗
    IMStove.Instance.LaunchUI(IMStove.LAUNCHUI_VALUE_EVENT, PrintLaunchUIResult);
    //获取配置信息，注意虽然 获取配置信息 与 初始化返回结构体一致，但需传不同代理实例用以区分不同返回
    IMStove.Instance.getConfigInfo(PrintConfigResult);
    IMStove.Instance.SetPushActive(true, PrintResult);
    IMStove.Instance.GetPushInfo(PrintPushResult);
}
	 
/**
  *演示从LaunchUI中获取 点击登出、删除游戏角色、退出游戏、删除游戏账号 回调
  */
public void TestGetCallbackFromLaunchUI()
{
    IMStove.Instance.SetLaunchActionCallBack(PrintLaunchActionResult);
}

public void PrintLaunchActionResult(IMStoveLaunchActionResult result)
{
    IMLog.Log("print result " + result.IMSDKRetCode);
    if(result.IMSDKRetCode == 1){//成功
        if(result.Type == 2){//IMStove.LAUNCHUI_ACTION_LOGOUT LaunchUI-设置界面中点击 登出 回调
           //todo
        }esle if(result.Type == 3){//IMStove.LAUNCHUI_ACTION_DEL_CHARACTER LaunchUI-设置界面中点击 删除游戏角色 回调
           //todo
        }esle if(result.Type == 7){//IMStove.LAUNCHUI_ACTION_EXIT_GAME LaunchUI-EXITPOPUP界面中点击 退出游戏 回调
           //todo
        }esle if(result.Type == 17){//IMStove.LAUNCHUI_ACTION_DEL_ACCOUNT LaunchUI-设置界面中点击 删除游戏账号 回调
           //todo
        }
    }
}

/**
*EXITPOPUP 可测试 退出游戏 回调
*/
public void TestLauchUI_EXITPOPUP_ActionCallback(){
    TestGetCallbackFromLaunchUI();
    IMStove.Instance.LaunchUI(7, PrintLaunchUIResult);
    
}

/**
*SETTING 可测试 登出、删除游戏角色、删除Stove账号 回调
*/
public void TestLauchUI_SETTING_ActionCallback(){
    TestGetCallbackFromLaunchUI();
    IMStove.Instance.LaunchUI(4, PrintLaunchUIResult);
}

/**
*申请、检查权限（仅支持Android）
*【建议在初始化完成之后，登录之前调用】
*请注意，该功能需与Android Native代码配合使用，如下"Permission Check in Android Native Part"
*/
public void TestPermissionCheck(){
    IMStove.Instance.PermissionCheck(PrintResult);
}

 =======================================Permission Check in Android Native Part Start=================================================
/**
*请注意，PermissionCheck功能需在主Activity中重写Activity onRequestPermissionsResult方法并调用IMSDKExtendStove.onRequestPermissionsResult
*/
 public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults)
  {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults);
    IMSDKExtendStove.onRequestPermissionsResult(requestCode, permissions, grantResults);
  }
 =======================================Permission Check in Android Native Part end=================================================
```





