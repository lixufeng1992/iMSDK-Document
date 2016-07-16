## MTO 统计功能说明

### MTO Extend 接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public void showPlatform() | 显示platform | √ | - |
| 4 | public void hidePlatform() | 隐藏platform | x | - |
| 5 | public void trackEvent() | 事件跟踪 | x | - |
| 6 | public bool trackPage() | 页面跟踪 | x | - |
| 7 | public void speedTest() | 测速 | x | - |
| 8 | public void reportCrash() | 获取当前登录返回数据 | x | - | 
| 9 | public void reportAutoExceptionReport() | 登出当前渠道 | x | - |


### MTO统计配置说明

 #### Android 端配置说明
 ``` xml
 <!-- MTO配置 APPSFLYER KEY，配置官网上获取 --> 
 <meta-data
      android:name="APPSFLYER_KEY"
      android:value="YOUR_APPSFLYER_KEY" />
<!-- MTO配置配置结束 -->
 ```