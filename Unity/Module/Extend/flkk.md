## 4.4.13.5 FLKK（飞流&Kakao）功能扩展

1、新增接口 ShowMessageBlockDialog

2、新增字段MsgBlocked

3、增加SendMultiChat()

4、邀请，发消息，发群消息接口，回调retMsg字段返回了kakao的错误码和错误信息，格式：
"thirdCode="+errorResult.getErrorCode() + "&thirdMsg="+errorResult.getErrorMessage()
如：
"Unknown:thirdCode=-401&thirdMsg=Application Session is Closed."       （其中Unknown: 为imsdk base包自动添加）



### 飞流九龙战更新：

| 更新点 | 更新内容 | 所属模块 |