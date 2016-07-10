# Beacon 功能说明
## Beacon 登录功能说明

### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | x | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | x | - |
| 3 | public void reportEvent | 事件上报 | x | - |
| 4 | public void reportPurchase() | 购买行为上报 | x | - |
| 5 | public void trackEvent() | 事件跟踪 | x | - |
| 6 | public bool trackPage() | 页面跟踪 | x | - |
| 7 | public void speedTest() | 测速 | x | - |
| 8 | public void reportCrash() | 获取当前登录返回数据 | √ | - | 
| 9 | public void reportAutoExceptionReport() | 登出当前渠道 | √ | - |


### Bugly统计配置说明

 #### Android 端配置说明
 ``` xml
 <!-- Bugly配置，配置官网上获取的APPID，注意：需要在APPID之前添加字符串：“bugly”--> 
<meta-data
    android:name="APPID_BUGLY"
    android:value="bugly900003637" /> 
<!-- Bugly配置结束 -->
 ```