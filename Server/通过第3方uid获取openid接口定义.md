## 7.3 通过ChannelId获取Openid接口定义

测试服接口url：[http:\/\/srvapi-beta.itop.qq.com\/v1.0\/user\/getAccount](http://srvapi-beta.itop.qq.com/v1.0/user/getAccount)

入参数：如输入参数表

返回：如返回参数表

规范：游戏配置必须打开iAllowQueryOpenidByChannelId开关

返回：如返回参数表

Host配置：

```
      10.197.93.56 srvapi-beta.itop.qq.com（内网）
      203.205.147.224 srvapi-beta.itop.qq.com（外网） 

```

正式服接口Url：[http:\/\/srvapi.itop.qq.com\/v1.0\/user\/getAccount](http://srvapi.itop.qq.com/v1.0/user/getAccount)

Host配置：虚ip 对应的 srvapi.itop.qq.com 服务

下面鉴权间的参数传递关系

\/\/输入参数表

| **入参数据类型说明** |  |  |
| :--- | :--- | :--- |
| \*user\_name | String | 37wan数据,对应的ChannelId;37wan\_web此处值填{user\_name},37wan客户端此处值填｛user\_id} |
| \*iGameId | Int | 登录鉴权时必填 |
| \*iChannel | Int | 第3方渠道标识,第3方渠道标识,1fb,2apple,3google,5guest,6zalo,7 37wanweb, 8 37wanapp, 9 link |
| \*iPlatform | Int | 来源平台定义1ios,2android,3web |
| \*sValidKey | string | 鉴权请求安全的Key; 生成方式请咨询iMSDK官方客服 |

\/\/返回正确返回参数

| **返回参数数据类型说明** |  |  |
| :--- | :--- | :--- |
| \*code | int | 返回值1，成功 |
| \*iOpenid | String | 游戏账号id uint64 |
| Desc | string | 说明 |

返回值格式：json格式，如下

{

"code": 1,

"desc": "SUCCESS",

"iOpenid": 1744830475,

}

错误返回

| **返回参数数据类型说明** |  |  |
| :--- | :--- | :--- |
| \*code | int | 返回值1，成功 |
| Desc | string | 错误对应的原因 |

返回值格式：

json格式，如下

{

code: -1103,

desc: "get 37wan user info is failure!"

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

