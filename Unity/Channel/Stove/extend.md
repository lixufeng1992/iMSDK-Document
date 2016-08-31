# Toy扩展(ToyExtend)

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
###iMSDK基础返回结构体
* iMSDK基础返回结构体  <font color=blue>IMResult</font>

| 变量 | 说明 |
| :-- | :-- |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg| 错误信息 |
| public int IMSDKRetCode| iMSDK返回码 ，1 为成功，其他为失败  |
| public int IMSDKRetMsg|  iMSDK 返回信息 |
| public int ThirdRetCode| 第三方返回码 |
| public int ThirdRetMsg| 第三方返回信息|
| public int RetExtraJson| 扩展信息 |

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


* IMStove方法类 <font color=blue> IMStove </font>

| 函数名 | 函数说明 |
| :-- | :-- |
| public void Initialize (IMStoveConfigCallback callback) | 初始化方法，在调用其他函数之前必须调用该函数 |
| public void LaunchUI (int uiType, IMStoveLaunchUICallBack callback, int noticeParam = 0) | 展示弹窗|
| public void getConfigInfo (IMStoveConfigCallback callback) | 获取配置信息 |
| public void SetPushActive (bool isActive, IMStoveCallBack callback) | 设置推送开关 |
| public void GetPushInfo (IMStovePushBack callback) | 获取推送开关 |

## 代码示例

```cs
    public void PrintResult(IMResult result){
        IMLog.Log("print result " + result.IMSDKRetCode);
        //输出，打印到屏幕上
        mResultDisplay = "AuthCallback:"
        + "\n ret code : " + result.IMSDKRetCode
        + "\n ret msg : " + result.IMSDKRetMsg
        + "\n third code : " + result.ThirdRetCode
        + "\n third msg : " + result.ThirdRetMsg;
	}

    public void PrintLoginCallCallback(IMStoveConfigResult result)
    {
        IMLog.Log("print result " + result.IMSDKRetCode);
        //输出，打印到屏幕上
        mResultDisplay = "AuthCallback:"
        + "\n ret code : " + result.IMSDKRetCode
        + "\n ret msg : " + result.IMSDKRetMsg
        + "\n third code : " + result.ThirdRetCode
        + "\n third msg : " + result.ThirdRetMsg
        + "\n gameip :" + result.GameIp
        + "\n gameport" + result.GamePort;
    }

	public void PrintConfigResult(IMStoveConfigResult result){
        IMLog.Log("print result " + result.IMSDKRetCode);
        //输出，打印到屏幕上
        mResultDisplay = "AuthCallback:"
        + "\n ret code : " + result.IMSDKRetCode
        + "\n ret msg : " + result.IMSDKRetMsg
        + "\n third code : " + result.ThirdRetCode
        + "\n third msg : " + result.ThirdRetMsg
        + "\n gameip :" + result.GameIp
        + "\n gameport" + result.GamePort;
	}

	public void PrintLaunchUIResult(IMStoveLaunchUIResult result){
        IMLog.Log("print result " + result.IMSDKRetCode);
        //输出，打印到屏幕上
        mResultDisplay = "AuthCallback:"
        + "\n ret code : " + result.IMSDKRetCode
        + "\n ret msg : " + result.IMSDKRetMsg
        + "\n third code : " + result.ThirdRetCode
        + "\n third msg : " + result.ThirdRetMsg
        + "\n uiNum :" + result.UiNum
        + "\n uiNum :" + result.UiNum
        + "\n portrait :" + result.Portrait
        + "\n accessToken :" + result.AccessToken
        + "\n memberId :" + result.MemberId
        + "\n nickName :" + result.NickName
        + "\n memberNo :" + result.MemberNo
        + "\n accountType :" + result.AccountType;
	}

        void Start() {
         IMLog.setLevel (IMLog.Level.Log);
         IMSDKApi.Stove.Initialize(PrintLoginCallCallback);
       }

        void Test() {
            /*
            *展示弹窗
            */
            IMStove.Instance.LaunchUI(IMStove.LAUNCHUI_VALUE_EVENT, PrintLaunchUIResult);

           /*
             *获取配置信息，注意虽然 获取配置信息 与 初始化返回结构体一致，但需传不同代理实例用以区分不同返回
             */
            IMStove.Instance.getConfigInfo (PrintConfigResult);
            IMStove.Instance.SetPushActive (true, PrintResult);
            IMStove.Instance.GetPushInfo (PrintPushResult);
         }


```





