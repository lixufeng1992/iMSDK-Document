## Adjust 工程配置

### 配置说明

*    权限配置，在AndroidManifest.xml中增加如下权限

     ```xml
     <uses-permission android:name="android.permission.INTERNET" />

     <!--可选-->
     <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
     ```

*    Adjust 信息配置

     ```xml
     <meta-data
                 android:name="IMSDK_STAT_ADJUST_APP_TOKEN"
                 android:value="{your_adjust_app_token}" />
     ```

*    Receiver 配置，在 Application 节点下，添加相应的配置。

     ``` xml 
     <!--可选,记录安装来源-->
     <receiver
                 android:name="com.adjust.sdk.AdjustReferrerReceiver"
                 android:exported="true" >
                 <intent-filter>
                     <action android:name="com.android.vending.INSTALL_REFERRER" />
                 </intent-filter>
     </receiver>	
     ```
*    Google 服务版本配置，Adjust 依赖 Google ADID 确认设备唯一性

     ```xml
       <meta-data android:name="com.google.android.gms.version"
       	android:value="@integer/google_play_services_version" />
     ```


 
