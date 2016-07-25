# Beacon 功能说明

## Beacon 登录功能说明

### 统计支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| 1 | public bool Initialize\(\) | 初始化方法 | √ | - |
| 2 | public bool Initialize\(IMStatChannelLists channelLists\) | 初始化方法 | √ | - |
| 3 | public void reportEvent | 事件上报 | √ | - |
| 4 | public void reportPurchase\(\) | 购买行为上报 | x | - |
| 5 | public void trackEvent\(\) | 事件跟踪 | x | - |
| 6 | public bool trackPage\(\) | 页面跟踪 | x | - |
| 7 | public void speedTest\(\) | 测速 | √ | - |
| 8 | public void reportCrash\(\) | 获取当前登录返回数据 | √ | - |
| 9 | public void reportAutoExceptionReport\(\) | 异常上报 | √ | - |

### Beacon 统计配置说明

#### Android 端配置说明

```xml
<!-- DENGTA配置，官网上获取的APPKEY --> 
<meta-data
    android:name="APPKEY_DENGTA"
    android:value="0I40061SZ81FIQ8L" />
<!-- DENGTA配置结束 -->
```

