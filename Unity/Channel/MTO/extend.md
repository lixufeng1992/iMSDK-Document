## MTO 统计功能说明

### MTO Extend 接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
| 2 | public void showPlatform() | 显示platform | √ | - |
| 4 | public void hidePlatform() | 隐藏platform | √ | - |

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




 #### Android 端配置说明
 ``` xml
 <!-- MTO配置 APPSFLYER KEY，配置官网上获取 --> 
 <meta-data
      android:name="APPSFLYER_KEY"
      android:value="YOUR_APPSFLYER_KEY" />
<!-- MTO配置配置结束 -->
 ```