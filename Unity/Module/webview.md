## 4.4.11 内置浏览器(WebView)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMWebViewLite | 1.WebView包括【普通】、【带工具栏】及【系统浏览器】3种模式<br>2.【普通模式】：无UI，关闭需调接口IMSDKApi.WebViewLite.Close()来实现<br>3.【带工具栏模式】：有UI，具有 关闭、前进、刷新等功能按钮<br>4.【系统浏览器模式】：用系统浏览器打开|

<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMWebViewLite（GameObject）上，开发者不要主动销毁该对象！</font>


### 浏览器基本功能

包括打开、关闭、设置大小等功能，这里不再赘述

### 获取网络票据

可以通过函数回调获取网络票据，获取票据之后，可以通过网络票据用于网页登录授权

```cs
public void GetTicket(WebViewTicketCallback callback=null)
```

<font color=red>注意：如果用户没有登录，无法获取票据</font>

### 工程配置说明

#### Android工程配置说明

```cs
<uses-permission android:name="android.permission.INTERNET" />
 <!-- webview start -->
    <activity
        android:name="com.tencent.imsdk.webview.JumpShareActivity"
        android:theme="@android:style/Theme.Translucent.NoTitleBar" >
    </activity>
    <activity
        android:name="com.tencent.imsdk.webview.qq.WebViewWithFavActivity"
        android:configChanges="orientation|screenSize|keyboardHidden|navigation|fontScale|locale"
        android:process=":imsdk_inner_webview"
        android:theme="@android:style/Theme.Dialog"
        android:windowSoftInputMode="adjustPan" >
    </activity>
<!-- IMSDK 内置浏览器  服务器地址(com.tencent.imsdk.SdkServer + 版本 + /user) -->
    <meta-data
        android:name="com.tencent.imsdk.webviewTicketServer"
        android:value="/user" />
	<meta-data
        android:name="com.tencent.imsdk.webview.ShowQQInfosInToolbar"
        android:value="\ false" /><!-- 是否展示QQ浏览器信息开关，不填或false为关，true为开 -->
<!-- webview end -->
```

#### iOS工程配置说明

> 主要需要修改目标iOS工程plist文件、IMSDKAppSetting.bundle文件中的配置，具体内容可参考渠道功能文档。
    
### 参考

* 网络票据结构体 <font color=blue>IMWebViewTicketResult</font>

| 变量 | 说明 |
| -- | -- |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public string Ticket | 网络票据 |

* 获取网络票据回调代理函数 <font color=blue>WebViewTicketCallback</font>

| 类型 | 说明 |
| -- | -- |
| public delegate void WebViewTicketCallback(IMWebViewTicketResult result) | 获取网络票据回调函数，返回网络票据返构体 |

* 浏览器状态结构体 <font color=blue>IMWebViewStatusResult</font>

| 变量 | 说明 |
| -- | -- |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public bool IsOpen | 是否显示 |
| public bool CanGoBack | 是否可后退，用户控制自定UI |
| public bool CanGoForward | 是否可前进，用户控制自定UI |

* 获取浏览器状态回调代理函数 <font color=blue>IMWebViewStatusResult</font>

| 类型 | 说明 |
| -- | -- |
| public delegate void WebViewStatusCallback(IMWebViewStatusResult result) | 获取浏览器回调函数，返回浏览器状态结构体 |

* 浏览器事件结构体 <font color=blue>IMWebViewActionResult</font>

| 变量 | 说明 |
| -- | -- |
| public int RetCode | 返回码，1 为成功，其他为失败 |
| public string ErrorMsg | 错误信息 |
| public bool StateCode | 1:打开事件 2：关闭事件 3：more...|

* 获取浏览器事件回调代理函数 <font color=blue>IMWebViewActionResult</font>

| 类型 | 说明 |
| -- | -- |
| public delegate void WebViewActionCallback(IMWebViewActionResult result) | 获取浏览器回调函数，返回浏览器事件结构体 |

* 内置浏览器方法类 <font color=blue>IMWebViewLite</font>

| 函数名 | 函数说明 |
| -- | -- |
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数 |
| public bool SetScreenType(bool isLandscape) | Android 设定屏幕方向 |
| public bool SetCenter (bool center) | 设定居中显示。在设定绝对位置后，该属性将会失效 |
| public void SetFullScreen(bool _isFullScreen) | 设置全屏 |
| public void SetSize (int w, int h) | 设定高宽大小，以像素为单位 |
| public void SetX (int x) | 设定X坐标位置，以像素为单位 |
| public void SetY (int y) | 设定Y坐标位置，以像素为单位 |
| public void SetPosition(int x, int y, int w, int h) | 设定绝对位置，以像素为单位 |
| public void OpenUrl (<br>&emsp;&emsp;string url, <br>&emsp;&emsp; bool needToolbar=false, <br> &emsp;&emsp; bool useBrowser = false<br>&emsp;&emsp;) | 显示浏览器<br> url 链接 <br> needToolbar 是否需要工具栏 <br> useBrowser 是否用系统浏览器打开 |
| public void Close () | 关闭浏览器 |
| public void GoBack() | 后退 |
| public void Forward() | 前进 |
| public void Reload() | 重新加载 |
| public void GetStatus(<br>&emsp;&emsp;WebViewStatusCallback callback=null<br>&emsp;&emsp;) | 获取浏览器状态 |
| public void GetTicket(<br>&emsp;&emsp;WebViewTicketCallback callback=null<br>&emsp;&emsp;) | 获取WebView登陆凭证 |
| public void SetWebViewActionCallback(<br>&emsp;&emsp;WebViewActionCallback callback<br>&emsp;&emsp;) | 监听WebView事件回调(打开、关闭等) |

### 代码示例

```cs
/**
*获取票据回调
*/
void OnGetTicket(IMWebViewTicketResult result) {
		testInfo = "code : " + result.RetCode
			+ "\nmessage : " + result.ErrorMsg;
		if (result.RetCode == 1) {
			testInfo += "\n" + result.Ticket;
		}
	}

/**
*获取状态回调(可前进、可回退等)
*/
void OnGetStatus(IMWebViewStatusResult result) {
		testInfo = "code : " + result.RetCode
			+ "\nmessage : " + result.ErrorMsg;
		if (result.RetCode == 1) {
			testInfo += "\nis open : " + result.IsOpen;
			testInfo += "\ncan go back : " + result.CanGoBack;
			testInfo += "\ncan go forward : " + result.CanGoForward;
		}
	}

/**
*获取事件回调(webview打开、关闭等)
*RetCode：1成功 其他为失败
*StateCode：1打开 2关闭 3... 
*/
void OnAction(IMWebViewActionResult result) {
		testInfo = "retCode : " + result.RetCode + " retMsg : " + result.ErrorMsg + 
				   "\n imsdkRetCode : " + result.IMSDKRetCode + " imsdkRetMsg : " + result.IMSDKRetMsg +
				   "\n thirdRetCode : " + result.ThirdRetCode + " thirdRetMsg : " + result.ThirdRetMsg +
					"\n stateCode : " + result.StateCode;
		IMLog.Log ("unity  sample OnAction callback: " + testInfo);
	}
    
void Start() {
    IMSDKApi.WebViewLite.Initialize ();
    //设置监听webview事件
    IMSDKApi.WebViewLite.SetWebViewActionCallback(OnAction);
}

/**
*获取票据
*/
void DoGetTicket(){
    IMSDKApi.WebViewLite.GetTicket(OnGetTicket);
}

/**
*设置高宽大小
*/
void DoSetSize(){
    IMSDKApi.WebViewLite.SetSize(800, 600);
}

/**
*设置是否屏幕居中
*/
void DoSetCenter(){
    IMSDKApi.WebViewLite.SetCenter(true);
}

/**
*打开【普通模式】WebView
*/
void DoOpenUrl(){
    IMSDKApi.WebViewLite.OpenUrl("http://itop.qq.com");
}

/**
*关闭【普通模式】WebView
*/
void DoSetCenter(){
    IMSDKApi.WebViewLite.Close();
}

/**
*全屏、居中、打开【带工具栏模式】WebView
*/
void DoOpenUrlWithToolBar(){
    IMSDKApi.WebViewLite.SetCenter(true);
	IMSDKApi.WebViewLite.SetSize(Screen.width, Screen.height);
	IMSDKApi.WebViewLite.SetFullScreen (true);
	IMSDKApi.WebViewLite.OpenUrl("http://www.qq.com", true,false);
}

```

