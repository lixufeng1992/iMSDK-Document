##6.4.1 Midas 开发者中心配置

###A.模式一：游戏为外发模式（代理或投资公司）

  A.1:【提出需求】联系米大师产品jolinyang提出需求
  
  
  A.2:【接入配置】在支付渠道开发的同时可以前置进行服务器部署，接入配置等工作
  
    A.2.1:【支付渠道开发】支付渠道的开发工作，由米大师完成
    
    A.2.2:【服务器部署】将米大师的各类环境，部署到游戏指定机器上
    
    A.2.3:【接入配置】填写《海外版本接入信息备案表》（填写接入基础信息，渠道参数信息，结算组，业务组，以及物品信息）支付接入联系人：cherryma


  A.3:【沙箱联调】请参看开发文档《腾讯海外支付Midas购买游戏币SDK白皮书》
    A.3.1：sdk下载地址：http://midas.qq.com/SDK_download_V3
    
    A.3.2：如果需要接入imsdk/apollo，需要联调开始之前预留时间，将米大师侧的sdk包合入imsdk方可使用；
沙箱联调均在国内环境下进行，步骤2中的服务器部署环境不为改步骤的前置条件
   
   
  A.4:【现网部署】,将物品，渠道，账户等信息部署到海外目标服务器上，前置步骤为：服务器部署完成
    
    
  A.5:【现网联调】,现网环境下支付联调，联调通过后游戏才可上线


###B.模式二：游戏为自运营模式接入步骤
  A.1:【提出需求】联系米大师产品jolinyang提出需求


1. 注册Facebook账号
   
   首先，需要先注册Facebook账号。
   
   请到Facebook官网注册账号：[https://www.facebook.com](https://www.facebook.com)，并根据提示完成账号认证（Email或者手机认证）。
   
2. 激活开发者账号
   
   有了Facebook账号之后，浏览器中打开Facebook开发者中心，激活开发者账号：
   
   ![激活Facebook开发者账号](Images/Facebook/facebook_register_developer.png)
   
   同意协议并继续：

   ![同意协议并继续](Images/Facebook/facebook_register_developer_confirm.png)
   
   \*手机验证
   
   ![手机验证](Images/Facebook/facebook_register_developer_confirm_cellphone.png)
   
   完成注册
   
   ![完成注册](Images/Facebook/facebook_register_developer_done.png)
   
3. 新建应用
    
   点击右上角菜单栏，新增App
   
   ![新建App](Images/Facebook/facebook_add_new_app.png)
   
   我们使用基础配置。选择iOS、Android都是可以的，配置方式也基本一致，这里不做叙述
   
   ![采用基础模式](Images/Facebook/facebook_add_basic.png)
   
   填写基本信息，注意App类型要选择游戏（Game）
   
   ![填写基本信息](Images/Facebook/facebook_add_basic_app.png)
   
   完成验证后，就成功生成App了
   
4. 配置应用
   
   在Faceboook App管理端，点击Settings菜单，可以看到App的基础信息，并点击“Add Platform”添加应用平台
   ![新增应用平台](Images/Facebook/facebook_add_platform.png)
   
   新增iOS、Android平台（跟进需要进行选择）
   
   ![新增移动应用平台](Images/Facebook/facebook_add_platform_mobile.png)
   
   添加对应的配置，可以直接填写，也可以通过点击平台配置右上角的“Quick Start”按照指引进行配置
   
   ![添加平台配置](Images/Facebook/facebook_add_platform_config.png)
   
5. 添加用户权限

   确认（添加）测试权限，在应用发布之前，只有添加到权限列表或测试用户才能有权限使用Faceboook的相关功能
   
   ![添加测试用户](Images/Facebook/facebook_add_roles.png)

5. 配置iMSDK后台

   请到iMSDK管理段进行后台配置，联系人RTX：hirryli