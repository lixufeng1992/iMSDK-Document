### Android配置管理

* 权限管理
```xml
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```

* Receiver配置管理
```
    <receiver 
        android:name="it.partytrack.sdk.ReferrerReceiver"
        android:exported="true">
        <intent-filter>
            <action android:name="com.android.vending.INSTALL_REFERRER" />
        </intent-filter>
    </receiver>
```

*meta-data配置管理
```
    <meta-data
        android:name="com.google.android.gms.version"
        android:value="@integer/google_play_services_version" />
        <!-- appId and appKey value, for example: PARTYTRACK_APP_ID : 6960, PARTYTRACK_APP_KEY : 79d3114eb96d3d847e4a3707e6ea802c -->
    <meta-data android:name="PARTYTRACK_APP_ID" android:value="{your appId}" />
    <meta-data android:name="PARTYTRACK_APP_KEY" android:value="{your appKey}" />
```