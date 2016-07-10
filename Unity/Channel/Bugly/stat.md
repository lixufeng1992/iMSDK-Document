# Bugly 功能说明

## Bugly 登录功能说明

### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | √ | - |
| 3 | public bool SetChannel(string channel) | 设置登录渠道| √ | - |
| 6 | public void reportEvent | 事件上报 | √ | - |
| 7 | public void reportPurchase() | 购买行为上报 | √ | - |
| 8 | public void trackEvent() | 事件跟踪 | √ | - |
| 9 | public bool trackPage() | 判断用户是否已经登录 | √ | - |
| 10 | public void speedTest() | 自动登录 | √ | - |
| 11 | public void reportCrash() | 获取当前登录返回数据 | √ | - | 
| 12 | public void reportAutoExceptionReport() | 登出当前渠道 | √ | - |


### Bugly统计配置说明

 #### Android 端配置说明
 ``` xml
 <!-- Bugly配置，配置官网上获取的APPID，注意：需要在APPID之前添加字符串：“bugly”--> 
<meta-data
    android:name="APPID_BUGLY"
    android:value="bugly900003637" /> 
<!-- Bugly配置结束 -->
 ```