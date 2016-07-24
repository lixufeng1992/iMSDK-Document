<font color=orange> 由于Google Plus 谷歌官方即将放弃，建议直接新建 Play 应用，Play 应用也可以用 Plus 登录</font>

1. 建立应用

    进入 [Google Play 控制台](https://play.google.com/apps/publish/) ，新建应用

    ![New App](Images/Google/google_play_add_new.png)

2. 获取App ID

    ![Get app id](Images/Google/google_play_app_detail.png)

    对应AndroidManifest.xml文件配置项

    ```xml
    <meta-data android:name="com.google.android.gms.games.APP_ID" android:value="\ {YOUR_APP_ID}" />
    ```

3. 添加Google Play测试人员

    ![add google play tester](Images/Google/google_play_add_tester.jpeg)

    在游戏发布之前，只有测试人员才能登陆，<font color=red>并确认应用是处于可测试状态</font>

4. 跳转控制台

    在“游戏详情”中，找到对应的控Api控制台链接，点击跳转

    ![Goto console](Images/Google/google_play_app_goto_console.png)

    1. 添加测试权限

        ![Confirm permission](Images/Google/google_plus_add_tester.png)

 iMSDK后台需要获取用户的基础信息，所以需要添加权限，GooglePlus必须添加权限后测试，或者将app发布

 2. 确认API

 ![Confirm API](Images/Google/google_plus_confirm_api.png)

 确保上面的权限已经添加

 3. 建立 OAuth

 ![Add OAuth](Images/Google/google_plus_add_oauth.png)

 需要添加Android、Web两种，Android用于手机端登录，Web端用于iMSDK服务器获取用户信息

 4. 配置 OAuth

 ![Add OAth](Images/Google/google_plus_config_oauth.png)

 对于Android的OAuth，需要配置KeyStore的SHA1和包名，这两个值需要确保正确，否则登录流程将出现异常

 5. 获取 Server Client ID

 网络应用程序中的用户端ID即为Server Client ID，需要注意不是Android的那一个

 ![get client id](Images/Google/google_plus_get_client_id.png)

 对应AndroidManifest.xml文件配置项

 ```xml
 <meta-data android:name="com.google.android.gms.serverclientid" android:value="100xxxxxxx-xxxxxxxxxxx.apps.googleusercontent.com" />
 ```
 6. 下载Web认证json文件

 在OAuth的截图中，点击网络应用程式最右侧的下载按钮，将下载后的文件提供给iMSDK后台（RTX：hirryli）


