##VK Android 工程配置

###1、在res/values/strings.xml 下添加：

  ```
  <integer name="com_vk_sdk_AppId">{your_vk_appid}</integer>

  ```

###2、在 AndroidManifest中添加Activity声明：

  ```
   <activity android:name="com.vk.sdk.VKServiceActivity"
        android:label="ServiceActivity"
        android:theme="@style/VK.Transparent" />
  ```

