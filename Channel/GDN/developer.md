##GDN开发者中心配置    
###1.[官方参考](https://developers.google.com/app-conversion-tracking/)        
###2.获取conversionid,label等     
+ 登入[google adwords](https://accounts.google.com/ServiceLogin?service=adwords&continue=https://adwords.google.com/um/identity?sourceid%3Dawo%26subid%3Dcn-en-ha-rh-bkmp0~105314626495%26hl%3Dzh_CN&hl=zh_CN&ltmpl=signin&passive=0&skipvpage=true)     
+ 点击Tools进入conversions     
+ conversions页面下点击`+CONVERSION`    
+ 选择App,然后会出现一个App conversions对话框，根据需求选择，例如选择First open and in-app actions,然后根据平台选择   
+ 点击contiune进入到settings 界面，然后填写相关信息。注意其中的Mobile app栏填写，如果是ios且没发布则需要到itunes connect里查看apple id
+ 点击save and continue    
+ 在页面底部Set up your tracking method,然后再点击 put tracking code into the app，在对话框里就可看到ACTConversionReporter xxxx的代码，其中就包括conversionid与label等       


