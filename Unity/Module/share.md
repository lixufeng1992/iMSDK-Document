## 4.4.2 分享模块(Share)

### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Share | 用于分享，如朋友圈、Facebook等 |


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMShare（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门
1. [完成特定渠道配置](../../Channel/README.md)
2. 代码实例

  ```cs
  void Start() {
      IMSDKApi.Share.Initialize ();
      IMSDKApi.Share.SetChannel("Facebook");
  }

  void TestShareCallback(IMResult result) {
      if(result.RetCode == 1) {
          Debug.Log("share ok");
      }
      else {
          Debug.Log("share error : " + result.ErrorMsg);
      }
  }

  void TestShare() {

      content.Type = IMShareContent.ShareType.LINK_DIALOG;
      content.Title = "this is title";
      content.Content = "this is content";
      content.Link = "http://ieg.qq.com";

      /*
      *iMSDK Android 支持3种地址：
      *1.网络地址：以http打头
      *2.本地媒体，如手机相册:以content打头
      *3.本地决对路径：以file打头
      */
      content.ImagePath = "http://ossweb-img.qq.com/images/game/ieg/web201404/logo.png";
      content.ThumbImage = "http://ossweb-img.qq.com/images/game/ieg/web201404/roles/lol.png";
      //content.ThumbImage = "file:///storage/emulated/0/Tencent/QQfile_recv/share_f.jpg;

      IMSDKApi.Share.Share(content, TestShareCallback);
  }
  ```