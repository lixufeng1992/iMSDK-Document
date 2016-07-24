## GDN 功能说明


### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | :--: |:-------: | :-----: | :--: |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public bool Initialize(IMStatChannelLists channelLists)  | 初始化方法 | √ | - |
| 3 | public void reportEvent | 事件上报 | √ | - |
| 4 | public void reportPurchase() | 购买行为上报 | x | - |
| 5 | public void trackEvent() | 事件跟踪 | x | - |
| 6 | public bool trackPage() | 页面跟踪 | x | - |
| 7 | public void speedTest() | 测速 | x | - |
| 8 | public void reportCrash() | 获取当前登录返回数据 | x | - | 
| 9 | public void reportAutoExceptionReport() | 异常上报 | x | - |


