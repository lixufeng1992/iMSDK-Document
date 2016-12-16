## Facebook 分享功能说明

### 分享功能支持列表

| 序号 | 功能 | 是否支持 | 备注 |
| :--: | :--: | :----: | :--: |
| 1 | 分享文本-后台 |  √ | 需要publish_actions权限 |
| 2 | 分享文本-对话框 | x | - |
| 3 | 分享链接-后台 | √ | 需要publish_actions权限 |
| 4 | 分享链接-对话框 | √ | - |
| 5 | 分享图片-后台 | √ | 需要publish_actions权限 |
| 6 | 分享图片-对话框 | √ | - |

### 字段填写规则

| 分享类型 | 标题（Title）| 内容（Content）| 链接（Link）| 图片（ImagePath） | 缩略图（ThumbPath）| 扩展字段（ExtraJson） |
| :--: | :--: | :--: | :--: | :--: | :--: | -- |
| 文本（后台） | - | √ | - | - | - | - |
| 文本（对话框） | x | x | x | x | x | - |
| 链接（后台） | √ | √ | √ | √（网络链接） | - | 接收消息好友列表 |
| 链接（对话框） | √ | √ | √ | √（网络链接） | - | 接收消息好友列表 |
| 图片（后台） | - | - | - | √（本地路径）| - | 接收消息好友列表 |
| 图片（对话框） | - | - | - | √（本地路径）| - | 接收消息好友列表 |

扩展字段使用说明：

* 接收消息好友列表
  
  以JSON格式字符串传值，如：
  
  ```json
  {"friends":["123","234"]}
  ```
