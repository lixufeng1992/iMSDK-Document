## 7.6 获取用户信息接口

测试服接口url：[http:\/\/srvapi-beta.itop.qq.com\/v1.0\/user\/getUserInfo](http://srvapi-beta.itop.qq.com/v1.0/user/getUserInfo)

输入参数：如输入参数表

接口调用方式：GET

返回：如返回参数表

Host配置：

```
10.197.93.56 srvapi-beta.itop.qq.com（内网）
203.205.147.224 srvapi-beta.itop.qq.com（外网）  

```

正式服接口Url：[http:\/\/srvapi.itop.qq.com\/v1.0\/user\/getUserInfo](http://srvapi.itop.qq.com/v1.0/user/getUserInfo)

Host配置：虚ip 对应的 srvapi.itop.qq.com 服务

下面鉴权间的参数传递关系

\/\/输入参数表

| **入参数据类型说明** |  |  |
| :--- | :--- | :--- |
| \*sInnerToken | String | 内部Token标识，在后台系统通行的key |
| \*iOpenid | Uint64 | 全球统一用户标识 |
| \*iGameId | Int | 登录鉴权时必填 |
| \*iChannel | Int | 第3方渠道标识,1fb,2apple,3google,5guest |
| \*iPlatform | Int | 来源平台定义1ios,2android,3web |
| \*sValidKey | string | 鉴权请求安全的Key; 生成方式请咨询iMSDK官方客服 |

请求串： [http:\/\/srvapi-beta.itop.com\/v1.0\/user\/getUserInfo?iChannel=13&iPlatform=3&sRefer=monitorAccountRightTest&iGameId=61&sInnerToken=0d7c721707ebafb64facb1569397c2f0&iOpenid=17793140&sValidKey=9790e7e358b860a3c68465fd6a40de02](http://srvapi-beta.itop.qq.com/v1.0/user/getUserInfo?iChannel=13&iPlatform=3&sRefer=monitorAccountRightTest&iGameId=61&sInnerToken=0d7c721707ebafb64facb1569397c2f0&iOpenid=17793140&sValidKey=9790e7e358b860a3c68465fd6a40de02)

\/\/返回正确返回参数

| **返回参数数据类型说明** |  |  |
| :--- | :--- | :--- |
| \*code | Int | 返回值1，成功 |
| \*desc | String | SUCCESS |
| \*iOpenid | UInt64\/Uint32 | 游戏账号id |
| \*sInnerToken | string | 内部Token标识，在后台系统通行的key |
| \*iGuid | UInt64 | 全球统一用户标识 |
| \*iChannel | Int | 渠道 |
| \*iGameId | Int | 游戏Id |
| \*sChannelId | String | 第3方用户id |
| \*iCount | Int | 此次拉取到的数量 |
| \*iExpireTime | int | 这是一个linux时间戳，表示Token有效期 |
| \*sUsername | String | 用户名（String） |
| \*iGender | Int | 性别\(int\) 0未定义,1男,2女2 |
| \*sBirthdate | String | 出生日期\(1987-2-23 11:33:33\) |
| \*sPictureUrl | String | 头像 |

如：

返回值格式：

json格式，如下

{

```
"code": 1,
"desc": "SUCCESS",
"iOpenid": 17793140,
"sInnerToken": "98a4e9761e974785a5ab7326723af347",
"iGuid": 1665373585913,
"iChannel": 13,
"iGameId": 61,
"sChannelId": "3f2d592f9856594ec93940ac0fb42a71",
"iExpireTime": 1461812955,
"sUserName": "pressure_6",
"sBirthdate": "",
"iGender": 1,
"sPictureUrl": "http:\/\/cdn.garenanow.com\/webmain\/static\/images\/avatars\/default.jpg"

```

}

错误返回

| **返回参数数据类型说明** |  |  |
| :--- | :--- | :--- |
| \*code | int | 返回值1，成功 |
| Desc | string | 错误对应的原因 |

返回值格式：

json格式，如下

{

code: -204,

desc: "user session is failure!"

}



# **请求安全加强及请求来源加强**

sValidKey算法

`<?php`

`//http://url/interface.php?A=asdfjk&Ba=1223&BB=321`

`//$params = $_GET;`

`//unset($params['sValidKey']);`

`$params['A']='asdfjk'; // ===>$_GET['A'] 来自传参`

`$params['Ba']='1223'; // ===>$_GET['Ba'] 来自传参`

`$params['BB']='321'; // ===>$_GET['BB'] 来自传参`

`$sKey = "2b3b1269df10e0b589fbcdc3d1891e28"; //sKey由imsdk server端接口人提供`

`echo getSValidKey($params, $sKey);`

`//获取sValidKey`

`function getSValidKey($params, $sKey)`

`{`

`$sParams='';`

`if(ksort($params))`

`{`

`//var_dump($params); //array (size=3) 'A' => string 'asdfjk' (length=6) 'BB' => string '321' (length=3) 'Ba' => string '1223' (length=4)`

`foreach($params as $k=>$v)`

`{`

`$sParams.=$v;`

`}`

`echo $sParams.=$sKey; //asdfjk32112232b3b1269df10e0b589fbcdc3d1891e28`

`return md5($sParams);`

`}`

`return false;`

`}`

`?>`

注：sKey请咨询iMSDK官方客服RTX:itop\_helper\(itop助手\)

