# Efun分享模块


## 分享功能支持列表

| 序号 | 功能 | 是否支持 | 备注 |
| :--: | :--: | :----: | :--: |
| 1 | 分享文本-后台 | x | |
| 2 | 分享文本-对话框 | x | - |
| 3 | 分享链接-后台 | x | |
| 4 | 分享链接-对话框 | √ | - |
| 5 | 分享图片-后台 | x | |
| 6 | 分享图片-对话框 | x | - |

## 字段填写规则

| 分享类型 | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson） |
| :--: | :--: | :--: | :--: | :--: | :--: | -- |
| 文本（后台） | x | x | x | x | x | x |
| 文本（对话框） | x | x | x | x | x | x |
| 链接（后台） | x | x | x | x | x | x |
| 链接（对话框） | √ | √ | √ | √ | - | 分享渠道 + description描述 |
| 图片（后台） | x | x | x | x| x | x |
| 图片（对话框） | x | x | x | x | x | x |

扩展字段使用说明：

* 指定分享渠道EfunShareType(默认Facebook)，和description描述文字(可选)
* 渠道与传参列表

| 分享渠道 | 渠道参数 |
| :--: | :--: |
| Facebook| Facebook |
| Twitter | Twitter |
| Kakao | kakao |
| VK | VK |
| Google | Google|
| Whatsapp | Whatsapp |
| Baha | Baha |
| Wechat | Wechat |
| Skype | Skype |
| ICQ | ICQ |
| Ithome | Ithome |
| Line | Line |


 以JSON格式字符串传值，如：
 ```code
 // convert dictionary to json string
 Dictionary<string, string> extra = new Dictionary<string, string>();
 extra.Add("description", "test description");
 extra.Add("EfunShareType","Facebook");
 content.ExtraJson = Json.Serialize(extra);
 ```

## 工程配置

### Android工程配置

* 参考Efun Login配置和依赖

### iOS工程配置

