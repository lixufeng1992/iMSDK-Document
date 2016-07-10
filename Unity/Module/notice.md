## 4.4.8 公告模块(Notice)
### 基础信息

| 命名空间 | 调用入口 |使用说明|
| :-- |:-- |:--|
| Tencent.iMSDK | IMSDKApi.Notice |从指定渠道拉取公告信息|


<font color=red>该类自动绑定在Unity的Tencent.iMSDK.IMNotice（GameObject）上，开发者不要主动销毁该对象！</font>

### 快速入门
1. [完成特定渠道配置](../../Channel/README.md)
2. 代码实例

```cs
void Start() {
    // 我们建议在游戏开始时就初始化登陆方法
    IMSDKApi.Notice.Initialize ();
    // 设定渠道可以根据自己的需要，在拉取公告之前设置
    IMSDKApi.Notice.SetChannel("imsdk");
}

// 拉取公告回调函数，处理登陆结果
void TestOnLoadNoticeCallback(IMLoadNoticeResult result){
        if(result.RetCode == 1) {
        Debug.Log("login ok, user open id is " + result.ToUnityString ());
    }
    else {
        Debug.Log("login error : " + result.ErrorMsg);
    }
}

void TestLoadNotice() {
    //调用拉取公告方法，参数定义参考函数说明部分
    IMSDKApi.Notice.LoadNoticeData("0.0.0.1","zh-TW",886,0,true, 1,"", TestOnLoadNoticeCallback);
}
``` 
###参考

* Noitce类方法 <font color=blue>IMNotice</font>   

| 函数名 | 函数说明 |     
| :-- | :-- |     
| public bool Initialize() | 初始化方法，在调用其他函数之前必须调用该函数  |      
|  public bool Initialize(string channel) |  指定某渠道进行初始化 |        
|public bool SetChannel(string channel)|channel为渠道名，传入“imsdk”表示为IMSDK的公告| 
| public string GetChannel() | 获取渠道  |   
| public void LoadNoticeData(string version, string language, int region, int partition, bool isUseCache,int noticeType=1, string extraJson=null, NoticeLoadCallback callback = null)|version    app版本<br>language   需要的语言环境**（见附：语言）**<br> region     地区**(见附：region)**<br>partition  游戏大区<br>isUseCache 如果有图片是否使用本地缓存图片<br>noticeType: 公告类型<li> 1 : 登录前公告</li><li> 2 : 登录后公告</li><li> 3 : 标题公告</li><li> 4 : 底部标题公告</li><li> 5 : 用户协议</li><li> 6 : 更新信息</li><br>extraJson  扩展字段<br> NoticeLoadCallback回调函数|      
|public void LoadNoticeData(string noticeId, int loadDataType = 1, string scene = null,int noticeType =1, string extraJson = null, NoticeLoadCallback callback = null)|加载公告:<br>noticeId:指定需要获取的notice ID(可选,如不指定将按loadDataType自动获取)<br> loadDataType: 1:从第三方渠道获取数据 2:从deepLink获取数据 3：预留：从imsdk自研平台获取数据（返回的是IMNoticeInfo）4...<br>scene:指定的场景<br>noticeType: 公告类型<li> 1 : 登录前公告</li><li> 2 : 登录后公告</li><li> 3 : 标题公告</li><li> 4 : 底部标题公告</li><li> 5 : 用户协议</li><li> 6 : 更新信息</li>extraJson:附加参数   | 
| public void ShowNotice(string noticeId, int noticeType = 1, string scene = null, string extraJson = null, NoticeShowCallback callback = null) | 展示公告:<br> noticeType: 公告类型<li> 1 : 登录前公告</li><li> 2 : 登录后公告</li><li> 3 : 标题公告</li><li> 4 : 底部标题公告</li><li> 5 : 用户协议</li><li> 6 : 更新信息</li><br>noticeId: 在后台配置的notice ID<br>scene:指定场景<br>extraJson:附加参数 |    
|public void SetUserTargetingData(IMUserTargetingData targetingData, string extraJson = null)|设置用户唯一标识码及标签|    
|public void UpdateUserTargetingDataToSvr(string extraJson = null)|将SetUserTargetingData的数据同步至服务器|     
|1public void CloseNotice(string noticeId = "", int closeType = 1, string extraJson = null)|关闭公告：<br> noticeId:指定需要关闭的notice ID(可选,如不指定将按closeType值关闭)<br>closeType:1：关闭最上端弹窗 2：关闭所有弹窗，包括等待中的弹窗|   
* 回调  

|回调函数名|回调说明|  
| :-- | :-- |  
| public delegate void NoticeLoadCallback(IMLoadNoticeResult result);|加载Notice回调，结果参考**IMLoadNoticeResult**|

  

* Notice结果  （IMLoadNoticeResult）

|属性|说明|  
| :-- | :-- |  
| public int retCode|返回码|   
|public string retMsg|返回信息|   
|public int imsdkRetCode|IMSDK返回码|    
|public string imsdkRetMsg|IMSDK返回信息|    
|public int thirdRetCode|第三方返回码|    
|public string thirdRetMsg|第三方返回信息|    
|public string retExtraJson|额外参数|  
|public string StateCode|状态码用以标记 加载公告数据时流程|    
|public int num|公告数|    
|public List &lt;IMNoticeInfo&gt; list|公告列表,内容参考**IMNoticeInfo**|



* Notice信息 (IMNoticeInfo) 

|属性|说明| 
| :-- | :-- |  
|public int NoticeId|公告Id|   
| public string AppId|AppID|   
| public string OpenIdt|用户openId|   
|public string NoticeUrl|公告跳转链接|    
|public int NoticeScene|公告展示的场景，管理端后台配置|    
|public int NoticeStartTime|公告有效期开始时间|   
|public int NoticeEndTime|公告有效期结束时间|    
|public int NoticeUpdateTime |公告更新时间|    
|public int NoticeContentType|公告内容类型:1:文本公告 2:图片公告 3:网页公告|    
|public string NoticeTitle|公告标题|    
|public string NoticeContent|公告内容|    
|public List&lt;IMNoticePic&gt; NoticePics|公告图片，参考**IMNoitcePic**|    
|public string NoticeContentWebUrl||   
|public string ExtraJson|扩展参数|


* Notice图片信息（IMNoitcePic）     

|属性|说明| 
| :-- | :-- |  
|public int NoticeId|用户姓名|   
|public int ScreenDir|屏幕方向1:横竖屏 2:竖屏 3:横屏|   
|public string MpicHash|图片hash值|   
|public string ExtraJson|扩展参数|    


### 代码示例  
* ####渠道说明     
通过设置不同渠道拉取不同来源的公告,例如imsdk表示从iMSDK拉取公告。    

```cs
  IMSDKApi.Notice.Initialize ();	//初始化
  IMSDKApi.Notice.SetChannel("imsdk");//设置渠道
```
* ####拉取公告

```cs 	
  IMSDKApi.Notice.Initialize ();	//初始化
  IMSDKApi.Notice.SetChannel("imsdk");//设置渠道
  IMSDKApi.Notice.LoadNoticeData("1.0.0","en",0,0,true, "",OnLoadNoticeCallback);  //拉取公告数据
		
```
###附:语言   

```
af-ZA	南非语
ar-AE	阿拉伯语(阿联酋)
ar-BH	阿拉伯语(巴林)
ar-DZ	阿拉伯语(阿尔及利亚)
ar-EG	阿拉伯语(埃及)
ar-IQ	阿拉伯语(伊拉克)
ar-JO	阿拉伯语(约旦)
ar-KW	阿拉伯语(科威特)
ar-LB	阿拉伯语(黎巴嫩)
ar-LY	阿拉伯语(利比亚)
ar-MA	阿拉伯语(摩洛哥)
ar-OM	阿拉伯语(阿曼)
ar-QA	阿拉伯语(卡塔尔)
ar-SA	阿拉伯语(沙特阿拉伯)
ar-SY	阿拉伯语(叙利亚)
ar-TN	阿拉伯语(突尼斯)
ar-YE	阿拉伯语(也门)
az-AZ	阿塞拜疆语(拉丁文,西里尔文)
be-BY	比利时语
bg-BG	保加利亚语
bs-BA	波斯尼亚语(拉丁文，波斯尼亚和黑塞哥维那)
ca-ES	加泰隆语
cs-CZ	捷克语
cy-GB	威尔士语
da-DK	丹麦语
de-AT	德语(奥地利)
de-CH	德语(瑞士)
de-DE	德语(德国)
de-LI	德语(列支敦士登)
de-LU	德语(卢森堡)
dv-MV	第维埃语
el-GR	希腊语
en-AU	英语(澳大利亚)
en-BZ	英语(伯利兹)
en-CA	英语(加拿大)
en-CB	英语(加勒比海)
en-GB	英语(英国)
en-IE	英语(爱尔兰)
en-JM	英语(牙买加)
en-NZ	英语(新西兰)
en-PH	英语(菲律宾)
en-TT	英语(特立尼达)
en-US	英语(美国)
en-ZA	英语(南非)
en-ZW	英语(津巴布韦)
es-AR	西班牙语(阿根廷)
es-BO	西班牙语(玻利维亚)
es-CL	西班牙语(智利)
es-CO	西班牙语(哥伦比亚)
es-CR	西班牙语(哥斯达黎加)
es-DO	西班牙语(多米尼加共和国)
es-EC	西班牙语(厄瓜多尔)
es-ES	西班牙语(国际)
es-GT	西班牙语(危地马拉)
es-HN	西班牙语(洪都拉斯)
es-MX	西班牙语(墨西哥)
es-NI	西班牙语(尼加拉瓜)
es-PA	西班牙语(巴拿马)
es-PE	西班牙语(秘鲁)
es-PR	西班牙语(波多黎各(美))
es-PY	西班牙语(巴拉圭)
es-SV	西班牙语(萨尔瓦多)
es-UY	西班牙语(乌拉圭)
es-VE	西班牙语(委内瑞拉)
et-EE	爱沙尼亚语
eu-ES	巴士克语
fa-IR	法斯语
fi-FI	芬兰语
fo-FO	法罗语
fr-BE	法语(比利时)
fr-CA	法语(加拿大)
fr-CH	法语(瑞士)
fr-FR	法语(法国)
fr-LU	法语(卢森堡)
fr-MC	法语(摩纳哥)
gl-ES	加里西亚语
gu-IN	古吉拉特语
he-IL	希伯来语
hi-IN	印地语
hr-BA	克罗地亚语(波斯尼亚,黑塞哥维那)
hr-HR	克罗地亚语
hu-HU	匈牙利语
hy-AM	亚美尼亚语
id-ID	印度尼西亚语
is-IS	冰岛语
it-CH	意大利语(瑞士)
it-IT	意大利语(意大利)
ja-JP	日语
ka-GE	格鲁吉亚语
kk-KZ	哈萨克语
kn-IN	卡纳拉语
ko-KR	朝鲜语
kok-IN	孔卡尼语
ky-KG	吉尔吉斯语(西里尔文)
lt-LT	立陶宛语
lv-LV	拉脱维亚语
mi-NZ	毛利语
mk-MK	马其顿语(FYROM)
mn-MN	蒙古语(西里尔文)
mr-IN	马拉地语
ms-BN	马来语(文莱达鲁萨兰)
ms-MY	马来语(马来西亚)
mt-MT	马耳他语
nb-NO	挪威语(伯克梅尔)
nl-BE	荷兰语(比利时)
nl-NL	荷兰语(荷兰)
nn-NO	挪威语(尼诺斯克)
ns-ZA	北梭托语
pa-IN	旁遮普语
pl-PL	波兰语
pt-BR	葡萄牙语(巴西)
pt-PT	葡萄牙语(葡萄牙)
qu-BO	克丘亚语(玻利维亚)
qu-EC	克丘亚语(厄瓜多尔)
qu-PE	克丘亚语(秘鲁)
ro-RO	罗马尼亚语
ru-RU	俄语
sa-IN	梵文
se-FI	萨摩斯语(芬兰)
se-NO	萨摩斯语(挪威)
se-SE	萨摩斯语(瑞典)
sk-SK	斯洛伐克语
sl-SI	斯洛文尼亚语
sq-AL	阿尔巴尼亚语
sr-BA	塞尔维亚语(拉丁文,西里尔文)
sr-SP	塞尔维亚(拉丁,西里尔文)
sv-FI	瑞典语(芬兰)
sv-SE	瑞典语
sw-KE	斯瓦希里语
syr-SY	叙利亚语
ta-IN	泰米尔语
te-IN	泰卢固语
th-TH	泰语
tl-PH	塔加路语(菲律宾)
tn-ZA	茨瓦纳语
tr-TR	土耳其语
tt-RU	鞑靼语
uk-UA	乌克兰语
ur-PK	乌都语
uz-UZ	乌兹别克语(拉丁文,西里尔文)
vi-VN	越南语
xh-ZA	班图语
zh-CN	中文(简体)
zh-HK	中文(香港)
zh-MO	中文(澳门)
zh-SG	中文(新加坡)
zh-TW	中文(繁体)
zu-ZA	祖鲁语     
```       
###附：区域（region）    

```    
1	美国|加拿大
1264	安圭拉
1268	安提瓜和巴布达
1242	巴哈马
1246	巴巴多斯
1441	百慕大
1284	英属维尔京群岛
1345	开曼群岛
1767	多米尼克
1809	多米尼加
1473	格林纳达
1876	牙买加
1664	蒙特塞拉特
1721	荷属圣马丁
1787	波多黎各
1869	圣基茨和尼维斯
1758	圣卢西亚
1784	圣文森特和格林纳丁斯
1868	特立尼达和多巴哥
1649	特克斯和凯科斯群岛
1340	美属维尔京群岛
1671	关岛
1670	北马里亚纳群岛
1684	美属萨摩亚
20	埃及
210	阿拉伯撒哈拉民主共和国
211	南苏丹
212	摩洛哥
213	阿尔及利亚
216	突尼斯
218	利比亚
220	冈比亚
221	塞内加尔
222	毛里塔尼亚
223	马里
224	几内亚
225	科特迪瓦
226	布基纳法索
227	尼日尔
228	多哥
229	贝宁
230	毛里求斯
231	利比里亚
232	塞拉利昂
233	加纳
234	尼日利亚
235	乍得
236	中非
237	喀麦隆
238	佛得角
239	圣多美和普林西比
240	赤道几内亚
241	加蓬
242	刚果(布)
243	刚果(金)
244	安哥拉
245	几内亚比绍
246	迪戈加西亚岛
247	阿森松岛
248	塞舌尔
249	苏丹
250	卢旺达
251	埃塞俄比亚
252	索马里
253	吉布提
254	肯尼亚
255	坦桑尼亚
256	乌干达
257	布隆迪
258	莫桑比克
260	赞比亚
261	马达加斯加
262	留尼汪|马约特
263	津巴布韦
264	纳米比亚
265	马拉维
266	莱索托
267	博茨瓦纳
268	斯威士兰
269	科摩罗
27	南非
290	圣赫勒拿
291	厄立特里亚
297	阿鲁巴
298	法罗群岛
299	格陵兰
30	希腊
31	荷兰
32	比利时
33	法国
34	西班牙
350	直布罗陀
351	葡萄牙
352	卢森堡
353	爱尔兰
354	冰岛
355	阿尔巴尼亚
356	马耳他
357	塞浦路斯
358	芬兰
359	保加利亚
36	匈牙利
370	立陶宛
371	拉脱维亚
372	爱沙尼亚
373	摩尔多瓦
374	亚美尼亚
37447	纳戈尔诺-卡拉巴赫
375	白俄罗斯
376	安道尔
377	摩纳哥
378	圣马力诺
379	梵蒂冈
380	乌克兰
381	塞尔维亚
382	黑山
384	科索沃
385	克罗地亚
386	斯洛文尼亚
387	波斯尼亚和黑塞哥维那
389	马其顿
39	意大利
40	罗马尼亚
41	瑞士
420	捷克
421	斯洛伐克
423	列支敦士登
43	奥地利
44	英国
441481	根西
441534	泽西
441624	马恩岛
45	丹麦
46	瑞典
47	挪威
48	波兰
49	德国
500	福克兰群岛
501	伯利兹
502	危地马拉
503	萨尔瓦多
504	洪都拉斯
505	尼加拉瓜
506	哥斯达黎加
507	巴拿马
508	圣皮埃尔和密克隆
509	海地
51	秘鲁
52	墨西哥
53	古巴
54	阿根廷
55	巴西
56	智利
57	哥伦比亚
58	委内瑞拉
590	瓜德罗普
591	玻利维亚
592	圭亚那
593	厄瓜多尔
594	法属圭亚那
595	巴拉圭
596	马提尼克
597	苏里南
598	乌拉圭
5993	圣尤斯特歇斯
5994	萨巴
5997	波内赫
5999	库拉索
60	马来西亚
61	澳大利亚
62	印尼
63	菲律宾
64	新西兰
65	新加坡
66	泰国
670	东帝汶
673	文莱
674	瑙鲁
675	巴布亚新几内亚
676	汤加
677	所罗门群岛
678	瓦努阿图
679	斐济
680	帕劳
681	瓦利斯和富图纳
682	库克群岛
683	纽埃
685	萨摩亚
686	基里巴斯|吉尔伯特群岛
687	新喀里多尼亚
688	图瓦卢|埃利斯群岛
689	法属波利尼西亚
690	托克劳
691	密克罗尼西亚联邦
692	马绍尔群岛
7	苏联|俄罗斯|哈萨克斯坦
81	日本
82	大韩民国
84	越南
850	朝鲜民主主义人民共和国
852	香港
853	澳门
855	柬埔寨
856	老挝
86	中国大陆
880	孟加拉国
886	台湾
90	土耳其
91	印度
92	巴基斯坦
93	阿富汗
94	斯里兰卡
95	缅甸
960	马尔代夫
961	黎巴嫩
962	约旦
963	叙利亚
964	伊拉克
965	科威特
966	沙特阿拉伯
967	也门
968	阿曼
970	巴勒斯坦
971	阿联酋
972	以色列
973	巴林
974	卡塔尔
975	不丹
976	蒙古
977	尼泊尔
98	伊朗
```