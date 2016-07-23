# MTA 统计功能说明

## MTA 统计功能说明

### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | :--: |:-------: | :-----: | :--: |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | √ | - |
| 3 | public void reportEvent | 事件上报 | √ | - |
| 4 | public void reportPurchase() | 购买行为上报 | x | - |
| 5 | public void trackEvent() | 事件跟踪 | √ | - |
| 6 | public bool trackPage() | 页面跟踪 | √ | - |
| 7 | public void speedTest() | 测速 | x | - |
| 8 | public void reportCrash() | 获取当前登录返回数据 | √ | - | 
| 9 | public void reportAutoExceptionReport() | 登出当前渠道 | √ | - |


### MTA统计配置说明

 #### Android 端配置说明
 ``` xml
<!-- MTA配置，包括在官网上获取的APPKEY和安装渠道 -->
<meta-data
    android:name="TA_APPKEY"
    android:value="AA4Z1K9BZN39" /> 
<!-- 请将value改为app发布的市场名称，如在GooglePlay就写GooglePlay< -->
<meta-data
    android:name="InstallChannel"
    android:value="GooglePlay" />
<!-- MTA配置结束 -->
 ```