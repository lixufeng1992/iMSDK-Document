## 4.4.13.2 Bulgy功能扩展

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.IMStatExtendBugly |Bugly扩展功能，包含自定义日志打印,添加场景关键数据|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMStatExtendBugly（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门

### 参考
* 接口说明

| 函数名 | 函数说明 | 备注 |
| :-- | :-- | :-- |
| SetLogCache() | 设置上报日志文件缓存大小，范围为0-30K，默认为10K | 仅支持Android平台 |
| BuglyLog() | 用以记录一些开发者关心的调试日志,这些日志在crash发生时将会自动上报 | - |
| BuglyPutUserData() | 崩溃发生时, 添加场景关键数据 | - |

###配置说明 

#### iOS 配置说明 
找到IMSDKAppSetting.bundle/Contents/Resources/app.plist文件，增加或修改如下配置：

```
 <key>Bugly</key>
 <dict>
 <key>unexpectedTerminatingDetection</key>
 <true/>
 <key>appid</key>
 <string>you_bugly_appid</string>
 </dict>
```

#### Android 配置说明

   [Android端配置参考](../../../Channel/Bugly/android.md)
