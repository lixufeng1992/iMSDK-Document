# Garena扩展（GarenaExtend）

## 命名空间

```cs
using Tencent.iMSDK
```

## 接口类

```cs
IMSDKApi.IMGarena
```

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMGarena（GameObject）上，开发者不要主动销毁该对象！</font>

## 模块使用说明
与iMSDKGarena登录模块配合使用

### 基本功能

主要 初始化、打开MShop、获取MShop链接信息等

## 工程配置说明

### Android工程配置说明

> 主要需要修改Assets/Plugins/Android/AndroidManifest.xml文件，具体内容可参考渠道功能文档。

### iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。

## 参考
###iMSDK基础返回结构体【iMSDK不同返回结构体都继承于IMResult】
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

* 回调代理函数 <font color=blue>无,IMResult为所有返回结构体基类</font>

###获取MShop关闭回调结构体及回调代理函数
*  获取MShop关闭回调结构体及回调代理函数  <font color=blue>IMGarenaMShopClosedCallBack(IMResult result) </font> 

| 类型 | 说明 |
| :-- | :-- |
| public delegate void IMGarenaMShopClosedCallBack(IMResult result) | 打开MShop，返回结构体 |

##方法函数说明
* IMGarena方法类 <font color=blue> IMGarena </font>
| 函数名 | 函数说明 |
| :-- | :-- |
| public void Initialize () | 初始化方法，在调用其他函数之前必须调用该函数 |
| public void OpenMShop (String region, int roleId, int serverId, IMGarenaMShopClosedCallBack callback) | 打开MShop|
| public string GetMShopLink(string region, int roleId, int serverId, bool embedded) | 获取MShop链接信息 |


##代码示例
```cs
public void PrintResult(IMResult result){
        IMLog.Log("print result " + result.RetCode);
	}

void Start() {
 IMGarena.Instance.Initialize();//init
 string yourMShopLink = IMGarena.Instance.GetMShopLink ("TW",1,1,true);// get mshop link
 
 /**
 *region: 请传"TW", 这个参数表示国家, TW, VN, TH, ID, SG, MY, PH, 会根据这个值跳转到不同的国家的mshop
 *serverId:  玩家选的区 (服) ;
 *roleId: 服务器中每个角色的ID;
 */
 IMGarena.Instance.OpenMShop ("TW",1,1,PrintResult);//open mshop
}
```





