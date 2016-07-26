# **iMSDK SERVER端----常见错误码**

1. -905是什么错误？

  -905 request illegal!   请求安全鉴权码计算错误，请检查客户端的配置，keystore、iGameId是否一一对应；

2. -205是什么错误？
  是用户登录态鉴权不通过或失效错误
  解决办法：
  1）客户端重新登录一次
  2）客户端重新登录还不能解决问题，则需要核对游戏客户端和GameSrv后端环境是否一致；
  工具：[检查openid所有的环境](https://open-beta.itop.qq.com/tools/env.php?imsdk_iOpenid=)


