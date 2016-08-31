## MTO Extend功能说明

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMMTO | MTO 扩展功能，包括用户用户信息、资料管理等 |

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMMTO（GameObject）上，开发者不要主动销毁该对象！</font>

### MTO Extend 接口列表
|序号|方法名|方法说明|是否支持|备注|   
|:--|:--|:--|:--|:--|
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public void showPlatform() | 显示platform | √ | - |
| 4 | public void hidePlatform() | 隐藏platform | √ | - |   
| 5 | public void ShowWeb(string roleName,string roleID, string level,string guild, string serverID,string key) | 显示MTO webview | √ | - |
| 6 | public void LoadUrl(string url) | 加载url | √ | - |

### MTO Extend接口说明
```
  showPlatform(int position)
  /**
  * showPlatform  显示platform
  * @param position  see as follow
  * TOP_LEFT = 1;
  * TOP_CENTER = 2;
  * TOP_RIGHT = 3;
  * RIGHT_CENTER = 4;
  * BUTTOM_RIGHT = 5;
  * BUTTOM_CENTER = 6;
  * BUTTON_LEFT = 7;
  * LEFT_CENTER = 8;
  * default : 1---TOP_LEFT
  */
```

```
  hidePlatform()
  /**
   * hidePlatform 隐藏platform
   */
```
##### 备注:要调用showPlatform和hidePlatform， 需在调用登录Initialize（）后再次调用Extend模块的Initialize（）

### MTO生命周期接口
> 游戏需在自己的入口activity中，在对应的接口调用下面的函数。

```
onActivityResult(int requestCode, int resultCode, Intent data)
/**
 * onActivityResult callback
 * @param requestCode requestCode
 * @param resultCode resultCode
 * @param data data
 */
    
```

```
onResume()         
```
