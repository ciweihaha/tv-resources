# tv-resources

电视直播、点播源、TVBox 配置和追剧资源的整理合集。数据来自下面三个仓库的公开内容，经过去重和清理后按分类存放。整理时间：2026-11-15。

## 文件一览

| 文件 | 内容 | 条数 |
|---|---|---|
| live/live-channels.json | 直播频道（电视 + 电台，正常内容，已去重；国内只留广东/河南/香港/澳门/台湾的省一级频道，深圳/东莞市台例外保留，儿童频道不限地域，国际不限；同名台最多留 2 条；不含购物/广告台、景区直播） | 3911 |
| live/live-channels-invalid.json | 标记为失效的频道，留着复查，不用于播放 | 304 |
| live/live-lines.json | 直播线路（TVBox 配置里的 lives 项，带 EPG/台标模板）+ 播放列表（全网搜索探活通过的 M3U/TXT 列表地址） | 37 条线路，170 条播放列表 |
| vod/vod-sources.json | TVBox 点播源（sites，去重后） | 825 |
| configs/config-files.json | TVBox 配置文件地址（raw + 镜像）与 spider 引擎、CMS 节点 | 90 个配置，8 个 spider，1 个 CMS 节点 |
| epg/epg-sources.json | EPG 模板、EPG id、EPG 播放列表地址、DIYP 接口、台标模板 | 3 个模板，1853 个 id，169 个列表，1 个 DIYP 接口，1 个台标模板 |
| guides/zhuiju-resources.json | 追剧资源（分类、评分、风险、验证记录） | 127 |

## 按地域精简直播频道（2026-11-15 15:24，用户指令；15:38 修正）

国内直播频道只留广东、河南、香港、澳门、台湾的台，其他国内的全部删除；国际频道不限，全留着。`live/live-channels.json` 从 9942 条精简到 2846 条，后恢复台湾频道并按官方/运营商源优选，现为 2906 条，再按“同名台最多留 2 条”去重，现为 2780 条，再删购物台和广告台，现为 2768 条：

- 保留 2768 条：广东 139 条、河南 216 条、香港 68 条、澳门 13 条、台湾 82 条、国际 2250 条。
- 删除 7096 条国内频道（不含广东/河南/香港/澳门的央视、各省卫视、地方台、运营商专线、中国广播、斗鱼等 7006 条，台湾地区频道 90 条）；后恢复台湾频道 85 条。
- 原文件已备份到本地 `~/workspace/resource-harvest/hourly/2026-11-15-1524-prune-backup-live-channels.json`，被删清单在同目录 `pruned-domestic-channels-2026-11-15.txt`（频道名 + 分组 + 地址前 80 字符），可恢复。以后每小时整理按此范围执行，已删的国内频道不再加回来。

### 台湾恢复、五地区优先官方与运营商源（2026-11-15 15:38，用户指令）

- 台湾频道恢复 85 条（上一轮删的 90 条里，5 条是误判的大陆频道未恢复：2 条中视购物、1 条江西九江年代音乐台、2 条非凡虎女王纪录片）。
- 广东、河南、香港、澳门、台湾这五个地区，同名频道有多条地址时优先留官方源（电视台/广电官网、官方 CDN，如凤凰 playtv-live.ifeng.com、RTHK 的 akamaized.net、台湾各台官方 YouTube 直播）与运营商源（移动/电信/联通专线、IPv6 移动地址 2409:8087 等、chinamobile.com / cmvideo.cn）；没有官方/运营商源时才留其他来源。本轮共去掉 25 条非官方非运营商的重复地址（广东 9、河南 5、香港 11）。五地区现存 640 条，其中官方/运营商源 180 条（广东 102、河南 34、香港 18、澳门 6、台湾 20）。

### 同名台最多留 2 条（2026-11-15 15:41，用户指令）

- 同一个台名（同一个频道）有多条不同地址时，最多保留 2 条；先按官方/运营商源优先排序，留优先的那 2 条，其余删掉。国际频道也一样，同名最多留 2 条。
- 本轮共去掉 126 条（广东 86、河南 22、香港 4、澳门 4、台湾 3、国际 7）。例如广东卫视从 44 条减到 2 条（均为移动 IPv6 运营商源），河南卫视从 24 条减到 2 条。现存 2780 条：广东 140、河南 218、香港 68、澳门 13、台湾 82、国际 2259。

### 购物/广告台删除（2026-11-15 15:43，用户指令）

- 购物台和广告台全部删除。购物台：名字含“购物”（欢腾购物、河南欢腾购物HD、深圳购物）、“Shopping”（Donna Shopping Tv、The Shopping Channel）、QVC 各台（日本、意大利、英国 QVC / QVC Beauty / QVC Extra / QVC Style / QVC UK）、Jewellery Maker（英国 Gemporia 珠宝购物台），共 12 条。
- 广告台：0 条。按“广告”“电视直销”“Infomercial”“Advert/Advertising/Ad channel”“Teleshopping”精确筛查，没有符合的台。注意：直接用子串 “Ad” 会误伤 181 条正常频道（BBC Radio、Radio Italia、Canada、Mad 等名字里含 “ad” 的电台/电视台），这些一律保留，没有删。
- JTV TV（韩国）是全州电视台（tvg-id JTV.kr），是正规地方台不是购物台，保留。
- 本轮共去掉 12 条购物台、0 条广告台。被删清单在本地 `~/workspace/resource-harvest/hourly/pruned-shopping-ad-channels-2026-11-15.txt`（频道名 + 分组 + 地址前 80 字符）。现存 2768 条：广东 139、河南 216、香港 68、澳门 13、台湾 82、国际 2250。以后每小时整理不再收购物台和广告台，已删的永不再加回来。

### 只留省一级频道（2026-11-15 16:09，用户指令）

- 五个地区（广东、河南、香港、澳门、台湾）只留省一级的频道，市台、县台、电台全部去掉；国际频道不动。
- 市台：名字含地级市名（广东 21 市、河南 18 市、台湾各县市）的台，共删 65 条。广东：东莞、佛山、广州、揭阳、汕头、深圳（含深圳卫视 4K/HD/高清、深圳国际/少儿/电视剧/财经/都市等）、潮州等市台 47 条；河南：郑州 1–6 频道、开封、新乡、濮阳、焦作（含睛彩焦作）、济源等市台 18 条。深圳卫视是市台（深圳广播电影电视集团，不是广东广播电视台），按规则删除。
- 县台：名字含“县”或河南县名/县级市名（上蔡、临颍、兰考、孟州、巩义、登封、禹州、长垣等）的台，共删 67 条，全在河南。
- 电台：名字或分组含“电台”“广播”“FM”“AM”“Radio”“之声”“之音”“调频”等的，共删 169 条。广东 79 条（中国广播分组的广通各市广播、广州/深圳/珠海/惠州/汕头/梅州/江门/清远/湛江/阳江各台广播、广东音乐之声、广东新闻频道 FM91.4 等）、河南 67 条（中国广播分组的河南交通/新闻/经济/音乐广播、郑州/洛阳/开封/安阳/南阳/商丘/信阳/许昌/漯河各市广播、河南广播电视台-MyRadio 等）、香港 14 条（RTHK 电台 1–5 台及普通话台、香港电台第一/二/三/五台、CNR 香港之声、AsiaFM、TalkonlyLive）、澳门 1 条（RádioMacau）、台湾 8 条（1766 線上電臺 2 条、BCC 中广新闻/流行/音乐、ICRT 2 条、羅東廣播電台）。
- 例外：“河南广播电视台-MyRadio”名字里虽有“广播电视台”，但它是 MyRadio 电台服务（qingting.fm 的 mp3 流，分组是中国广播），按电台删除。名字里带“广播”但实际是电视台官方名的条目，本轮没有（只有这一条，且已按电台处理）。
- 误判修正：欢笑剧场4K银河源被“河源”二字误判为河源市台（“银河源”的“河源”不是地名），已恢复；脚本已修（“银河源”里的“河源”不再算城市名）。
- 分类优先级：电台 > 县台 > 市台（一条同时符合多类的只计一次）。少数带城市名的广播频率（如东莞阳光1008、郑州活力944/车道931、深圳飞扬音乐971）计在市台里，但同样已删。
- 本轮共去掉 301 条（市台 65、县台 67、电台 169）。被删清单在本地 `~/workspace/resource-harvest/hourly/pruned-city-county-radio-2026-11-15.txt`（按市台/县台/电台分类，频道名 + 分组 + 地址前 80 字符）。现存 2467 条：广东 13、河南 64、香港 54、澳门 12、台湾 74、国际 2250。以后每小时整理只收省一级频道，市台/县台/电台不再加回来。
- 备注：广东剩 13 条里有 2 条不是省台频道（广东-丹霞山丹梯铁锁是景区直播、粤荟萃是合集频道），河南剩 64 条里有 8 条景区直播（云台山 4 条、八里沟 2 条、少林寺广场、郑东新区千玺广场），因不属于市台/县台/电台而保留；如需进一步去掉，由用户决定。

### 深圳、东莞市台例外保留 + 景区直播删除（2026-11-15 16:21、16:22，用户指令）

- 深圳、东莞的市台例外保留：从上一轮被删清单里把深圳、东莞的电视台恢复回来，共 14 条——深圳 12 条（深圳卫视 2 条、深圳卫视4K 2 条、深圳卫视HD、深圳卫视高清、深圳国际、深圳少儿、深圳电视剧、深圳移动、深圳财经、深圳都市），东莞 2 条（东莞新闻综合、东莞生活资讯）。恢复时按归一化 URL 去重，0 条重复。深圳/东莞的电台/广播频率（东莞阳光1008、深圳飞扬音乐971、各广播）不恢复；深圳购物（购物台）不恢复；广东-东莞中心广场、广东-深圳世界之窗是景区/广场直播，不恢复（见下）。
- 景区直播删除：凡是景区、景点、广场这类地方的实时直播画面（不是电视台频道），全部删掉，共 10 条——广东 2 条（广东-丹霞山丹梯铁锁、粤荟萃合集频道），河南 8 条（云台山小寨沟、云台山百家岩、云台山红石峡、云台山茱萸峰、八里沟天界山玻璃栈道、八里沟桃花湾瀑布、少林寺广场、郑东新区千玺广场）。被删清单在本地 `~/workspace/resource-harvest/hourly/pruned-scenic-2026-11-15.txt`（频道名 + 分组 + 地址前 80 字符）。
- 本轮净增 4 条（恢复 14 条 − 删除景区 10 条）。现存 2471 条：广东 25、河南 56、香港 54、澳门 12、台湾 74、国际 2250。同名台仍最多 2 条，无重复归一化地址。以后每小时整理：深圳、东莞的市台保留不删，景区直播不收不加，已删的永不再加回来。

### 儿童频道不限地域恢复（2026-11-15 16:28，用户指令）

- 儿童频道不管是哪个地区的都恢复：从地域精简前的完整备份（9942 条）里找出名字含“少儿”“卡通”“儿童”“幼幼”“亲子”“卡酷”“哈哈炫动”“金鹰卡通”的频道，以及 BesTV宝宝动画、优优宝贝，共 154 条候选；其中 26 条已在现文件里，缺失 128 条。
- 恢复 67 条，同名台最多留 2 条（按官方/运营商源优先排序，留前 2 条），其余 61 条不恢复。恢复清单在本地 `~/workspace/resource-harvest/hourly/restored-children-2026-11-15.txt`（频道名 + 分组 + 地址前 80 字符，按央视/广东/河南/港澳台/其他省/国际分）。
- 恢复的 67 条：央视 2 条（CCTV-14少儿，含“CCTV-14 少儿”同名归一后共 2 条）、河南 1 条（郑州5妇女儿童HD）、其他省 64 条（BTV卡酷少儿、北京卡酷少儿、卡酷少儿、哈哈炫动、上海哈哈炫动、湖南金鹰卡通、金鹰卡通、优漫卡通、江苏优漫卡通、嘉佳卡通、佳佳卡通、浙江少儿、山东少儿、济南少儿、南京少儿、成都少儿、江西少儿、河北少儿科教、甘肃少儿、黑龙江少儿、睛彩少儿、云南少儿、海南少儿、福建少儿、宁夏少儿、内蒙古少儿频道、少儿动漫、少儿动画、IPTV少儿动画、FZTV-4 Children 少儿频道、BesTV宝宝动画、优优宝贝等，各含 HD/SD/576p 变体时按同名最多 2 条计）。广东、港澳台、国际的儿童频道本轮 0 条——广东嘉佳卡通、深圳少儿已在文件里，港澳台和国际的儿童频道之前没删过。
- 未恢复的：3 条儿童电台不恢复（大连少儿广播、苏州儿童广播、长春少儿与老年生活广播，均为 qingting.fm 的 mp3 音频流，是电台不是电视频道）；MOMO亲子台、东森幼幼在完整备份里根本没有，无从恢复；“动画”“动漫”单独出现的不算儿童频道（SiTV动漫秀场、iHOT爱动漫、NewTV黑莓动画等是通用动漫台，不恢复），纪录片节目名里的“宝宝”（动物宝宝闯天涯等）和熊猫频道的幼儿园直播也不是频道，不恢复。
- 现存 2538 条：广东 25、河南 57、香港 54、澳门 12、台湾 74、国际 2250、央视及其他省儿童频道 66。同名台仍最多 2 条，无重复归一化地址。以后每小时整理：儿童频道不限地域（央视少儿、各省少儿/卡通频道都收），已恢复的儿童频道永不再删。

## 第十八批合并（2026-11-16 05:06，每小时整理）

本轮换用新关键词（iptv m3u8、tvbox json、epg xml、live tv playlist、m3u playlist、diyp、zhibo、tv channels）搜 GitHub，135 个仓库 25 个新仓库；其中资源类：akkradet/IPTV-THAI（泰国合集）、JulioCesarXY/EPG-LG-Channels（LG 美国 FAST 频道 + EPG，每 6 小时自动更新）、kuke31/xmlgz（Erw 国内节目单）、dbghelp/JCOM-TV-EPG（日本 JCOM 节目单）、karenda-jp/etc（日本节目单 guides.xml）；matthuisman 的 Samsung TV Plus 是 Channels DVR 集成工具、没有播放列表文件，未收。把新找到的 2 个播放列表（泰国 FREETV.m3u、LG 美国 lg_channels_us.m3u）下载解析，249 个频道条目按地域范围过滤后剩 226 个候选，逐条探活后 171 条新频道并入 live-channels.json；成人直播源本轮无新增：

- 新增频道 171 条：全部为国际频道（泰国 15 条：DLTV 1-5 等泰国数字电视；LG 美国 FAST 156 条：LiveNOW from FOX、Newsmax、Reuters、Fox Weather、BBC Drama/Top Gear/Adventure、ESPN 8、PBS 系列等；儿童频道 1 条：Kids TV）。现存 3911 条：广东 27、河南 57、香港 123、澳门 19、台湾 83、国际 3419、央视及其他省儿童频道 177，儿童频道共 242 条。同名台仍最多 2 条，无重复归一化地址。另：classify() 默认把未知分组判为国内频道，会误排除这两个已知外国列表，本轮对泰国与 LG 美国两个来源强制按国际频道处理（来源本身即为外国合集）。
- 新增播放列表 2 条：泰国 FREETV.m3u（akkradet/IPTV-THAI，53 条）、LG 美国 lg_channels_us.m3u（JulioCesarXY/EPG-LG-Channels，196 条）。新增 EPG 6 条：Erw 国内节目单 e.xml.gz（当天）与 all.xml.gz（七天回看，kuke31/xmlgz）、日本 JCOM 节目单 jcom.xml（dbghelp，21MB）、日本节目单 guides.xml（karenda-jp/etc，11MB）、LG 美国节目单 lg_epg_us.xml（JulioCesarXY）、泰国节目单 guide.xml（akkradet/IPTV-THAI），均实测为真 XMLTV。现存播放列表 170 条、EPG 列表 169 条、配置 90 个、点播源 825 条。
- 跳过：受限 13 条（泰国 Boomerang、Boom Cartoon 在 v2h-cdn 上 403，机房 IP 被挡；其余为 LG 的 Amagi/Wurl 限流地址）；不可达 39 条；死链 3 条。常查文件 TVA、Alplox、kakaxi iptv.txt、kakaxi ipv4.txt 与上轮逐字节相同，未重新解析；kilvn 直播与 EPG 断连第 14 轮；109.233.89.170 的 Adventure_HD 连续十四轮 403，机房 IP 被挡，留待家里测。

## 第十七批合并（2026-11-16 04:06，每小时整理）

本轮换用新关键词（iptv-playlist、tvbox、epg-xmltv、live-tv、iptv-channels、m3u8、tv-source、diyp-tv）搜 GitHub，191 个仓库 26 个新仓库；网页搜索发现 youhunwl/TVAPP（TVBox 源收集仓库）与 b.zhuiju.me 的 VMA 直播源列表，另从中挖出 24 个新地址；常查源的 README 共抽出 85 个地址，另补 13 个，探活 59 个，通过 46 个；新增播放列表 6 条、EPG 2 条、配置 14 条、点播源 28 条；又把新找到的 5 个播放列表（BDIX 孟加拉合集、BDIX 国际合集、GNTV 港台合集、zbds iptv4、jackTV）与更新过的 kakaxi ipv4 列表下载解析，5058 个频道条目按地域范围过滤后剩 879 个候选，逐条探活后 576 条新频道并入 live-channels.json；再把 zbds iptv4、jackTV、TV-IPV4 与 VMA 列表解析，79 个候选探活后 57 条新频道并入；成人直播源另进本地文件，本轮新增 309 条：

- 新增频道 633 条：国际 530 条（BDIX 的孟加拉/印巴与国际频道为主）、香港 46 条（jackTV 的 TVB 翡翠/明珠、HOY、ViuTV、RTHK 等，含字幕版）、澳门 5 条、台湾 8 条、广东 1 条（广东珠江 IPv6）、央视及其他省儿童频道 43 条，儿童频道共 71 条。现存 3740 条：广东 27、河南 57、香港 123、澳门 19、台湾 83、国际 3248、央视及其他省儿童频道 177，儿童频道共 241 条。同名台仍最多 2 条，无重复归一化地址。另：VMA 列表里的河南桐柏/郸城新闻综合是县台、广东番禺电视台是区级台，按只留省一级的规则未收（桐柏/郸城两个县名不在 prune 名单里，是漏网，已单独排除）。
- 新增播放列表 6 条：BDIX 孟加拉合集与国际合集（saeidrahmanbd/BDIX-IPTV）、GNTV 港台合集（YueChan/Live）、zbds iptv4（live.zbds.top，398 条）、jackTV（php.946985.filegear-sg.me，211 条，港台为主）、TV-IPV4（BurningC4/Chinese-IPTV，58 条）。新增 EPG 2 条：BDIX 的节目单（32MB）、Rakuten 英国节目单（dp247，6.7MB）。新增配置 14 条：jifeng250 的 tvbox.json 与 urls.json、2hacc 的 oktv.json、高天流云的 js.json、ztha 的 GYCK.json、kstore 的 wex.json 与 aowu.json、lushunming 的 index.json、chitue 的 dongliTV api.json（93 个点播源）、guot55 的 vip2.json、maoystv 的 000.json、xyq 的 XYQTVBox.json、FongMi.json、xhztv 的 DC.txt 多仓列表。新增点播源 28 条：OuonnkiTV（Yesbaiwan）与 ljfbin2 的 LibreTV 订阅单里的 CMS 接口（爱奇艺、iKun、猫眼、量子、极速、魔都、最大、无尽、新浪、速播、U酷、光速、红牛、如意、豪华、虎牙、茅台、360、非凡、金鹰、百度云、艾旦等），逐个探活确认返回 CMS JSON 后才并入。现存播放列表 168 条、EPG 列表 163 条、配置 90 个、点播源 825 条。
- 跳过：不可达 22 条（kilvn 的直播与 EPG 共 3 条断连，第 13 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；gitlab 的 dzhipy 与 fmys.top 的 TVBox 配置 404；jinenge 与 kkgithub 镜像连不上；aiyakuaile 的带账号密码示例地址连不上；TVAPP 里的 ufuzi 短剧接口、9877 的 api.json、hgyx、gitmirror、yingm 的配置连不上）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续十三轮 403，机房 IP 被挡，留待家里测）；非直链 38 条（GitHub blob 页面 4 个；iptv-doctor 的状态页 2 个；OuonnkiTV 与 jifeng250 的代理/镜像地址 13 个，只留 raw 版；kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；zbds 的 iptv6 是只有更新时间的空表，iptv4.txt 与 .m3u 同数据；yoursmile66 的 XC.json 是十六进制加密配置，内容无法验证；OuonnkiTV 的 lite/full 等 5 个订阅单与 ljfbin2 的 2 个订阅单是点播源列表，接口已单独抽进 vod-sources.json；成人配置 adult.json 不进公开仓库）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 39 条（已在库里 24 个；占位/示例地址 6 个；iptv-org 国家/分类变体 1 个；suxuang 的 refs/heads 镜像 2 个；bililive 直播间列表 1 个；电台列表 1 个；其余 4 个）。
- 频道探活说明：879 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），576 条通过；死链 13 条、不可达 157 条、受限 133 条未并入。3469 条国内非五地区频道按地域范围排除；346 条成人分组频道只进本地文件；同名已满 2 条的 61 条与同名超额 29 条未并入。额外 75 个候选（zbds/jackTV/VMA）探活后 57 条通过，不可达 17 条、受限 1 条未并入。成人文件新增 309 条（BDIX 国际合集的成人分组频道，逐条探活通过，如 Abella Danger、AJ Applegate 等），本地成人文件现为 40983 条。

## 第十六批合并（2026-11-16 03:06，每小时整理）

本轮换用新关键词（iptv-m3u、m3u-playlist、tvbox-config、free-iptv、epg-guide、diyp、zhibo、live-stream）搜 GitHub，140 个仓库 32 个新仓库；网页搜索无新发现（iptv-org、Free-TV、BuddyChewChew plex_all 均已在库里）；常查源的 README 共抽出 56 个地址，另补 13 个，探活 38 个，通过 19 个；新增播放列表 2 条、EPG 4 条、配置 0 条；又把新找到的两个播放列表（巴尔干合集、SuperTV）下载解析，697 个频道条目按地域范围过滤后剩 171 个候选，逐条探活后 98 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮新增 6 条：

- 新增频道 98 条：国际 36 条（巴尔干合集的 Pluto/Samsung FAST 频道、SuperTV 的菲律宾与美国 FAST 频道等）、儿童频道 62 条（Pluto/Samsung 的 Kids 频道等，不限地域收录）。现存 3107 条：广东 26、河南 57、香港 78、澳门 14、台湾 75、国际 2723、央视及其他省儿童频道 134，儿童频道共 170 条。同名台仍最多 2 条，无重复归一化地址。
- 新增播放列表 2 条：巴尔干免费合集（dbojan/free-iptv-balkan-plus，466 条）、SuperTV（fotvnetwork/iptv-free，231 条，菲律宾与美国 FAST 频道）。新增 EPG 4 条：Pluto TV 与 Samsung TV Plus 的节目单（matthuisman/i.mjh.nz）、tvprofil.net 的节目单、123tv 的节目单（interlark）。现存播放列表 162 条、EPG 列表 161 条。
- 跳过：不可达 17 条（kilvn 的直播与 EPG 共 3 条断连，第 12 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；日本合集的 7 个地址与日本 EPG 均 404，源仓库已不存在；aiyakuaile 的带账号密码示例地址连不上；something.com 的示例 EPG 地址 404）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续十二轮 403，机房 IP 被挡，留待家里测）；非直链 11 条（kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；balkan-plus 的国内子集与 123tv 的浅色版节目单是重复数据；SAT>IP 列表是 rtsp 调谐参数、需专用硬件不能直播；3 个成人播放列表只进本地文件）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 32 条（已在库里 24 个；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：171 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），98 条通过；死链 39 条、不可达 28 条、受限 6 条未并入。503 条国内非五地区频道按地域范围排除；1 条购物台排除；12 条同名已满 2 条未并入。Ahasan 的孟加拉/印巴合集无 #EXTM3U 头未收；binhex 的英文合集是 iptv-org 全表的语言子集未收；HaNoiIPTV 仓库根目录没有播放列表文件未收。成人文件新增 6 条（Izanami1618 的 +18 合集，如 Playboy、VENUS 等），本地成人文件现为 40674 条。

## 第十五批合并（2026-11-16 02:06，每小时整理）

本轮换用新关键词（m3u8、iptv-playlist、tvbox、live-tv、epg、free-tv、zhiboyuan、diyp-m3u）搜 GitHub，177 个仓库 0 个新仓库；网页搜索无新发现（iptv-org、Free-TV、BuddyChewChew plex_all 均已在库里）；常查源的 README 共抽出 36 个地址，另补 13 个，探活 17 个，通过 8 个但全部已在库里或按规则不收，播放列表/EPG/配置 0 新增；又把 TVA 自更新合集、Alplox 频道目录与 kakaxi 的两个列表重新下载解析（kakaxi iptv.txt 本轮有更新，其余 3 个文件与上轮逐字节相同），4056 个频道条目按地域范围过滤后剩 221 个候选，逐条探活后 1 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮 0 新增：

- 新增频道 1 条：国际 1 条（TVA：В мире животных，mcquack 流）。现存 3009 条：广东 26、河南 57、香港 78、澳门 14、台湾 75、国际 2687、央视及其他省儿童频道 72，儿童频道共 105 条。同名台仍最多 2 条，无重复归一化地址。
- 跳过：不可达 7 条（kilvn 的直播与 EPG 共 3 条断连，第 11 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；aiyakuaile 的带账号密码示例地址连不上）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续十一轮 403，机房 IP 被挡，留待家里测）；非直链 6 条（kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 32 条（已在库里 24 个；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：221 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），1 条通过；死链 27 条、不可达 188 条、受限 5 条未并入。TVA 的修订头条目与 101.ru 音频流各 1 条不属于电视频道，已排除。kakaxi 列表里的凤凰卫视中文/资讯/香港台（phenix.php 本轮 404，rtp 中继连不上）探活未通过，未并入。TVA 的 ♥18+ 分组 116 条不进公开频道表，且全部已在本地成人文件里，0 新增；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件仍为 40668 条。

## 第十四批合并（2026-11-16 01:06，每小时整理）

本轮沿用上一轮的 8 组关键词（m3u、iptv-channels、tv-live、epg-xml、tvbox-config、zhibo、live-stream、diyp）搜 GitHub，141 个仓库 0 个新仓库；常查源的 README 共抽出 36 个地址，另补 13 个，探活 17 个，通过 8 个但全部已在库里或按规则不收，播放列表/EPG/配置 0 新增；又把 TVA 自更新合集、Alplox 频道目录与 kakaxi 的两个列表重新下载解析（4 个文件与上轮逐字节相同），3419 个频道条目按地域范围过滤后剩 225 个候选，逐条探活后 2 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮 0 新增：

- 新增频道 2 条：国际 2 条（TVA：Комедийное HD、Сваты）。现存 3008 条：广东 26、河南 57、香港 78、澳门 14、台湾 75、国际 2686、央视及其他省儿童频道 72，儿童频道共 105 条。同名台仍最多 2 条，无重复归一化地址。
- 跳过：不可达 7 条（kilvn 的直播与 EPG 共 3 条断连，第 10 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；aiyakuaile 的带账号密码示例地址连不上）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续十轮 403，机房 IP 被挡，留待家里测）；非直链 6 条（kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 32 条（已在库里 24 个；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：225 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），2 条通过；死链 29 条、不可达 189 条、受限 5 条未并入。kakaxi 列表里的凤凰卫视中文/资讯/香港台（phenix.php）探活未通过，未并入。TVA 的 ♥18+ 分组 116 条不进公开频道表，且全部已在本地成人文件里，0 新增；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件仍为 40668 条。

## 第十三批合并（2026-11-16 00:06，每小时整理）

本轮换用新关键词（m3u、iptv-channels、tv-live、epg-xml、tvbox-config、zhibo、live-stream、diyp）搜 GitHub，141 个仓库里 1 个是之前没见过的新仓库（helin021798/helin-zhibodianshang，直播电商 Agent Skill，不是 IPTV 资源，不收录）；常查源的 README 共抽出 36 个地址，另补 13 个，探活 17 个，通过 8 个但全部已在库里或按规则不收，播放列表/EPG/配置 0 新增；又把 TVA 自更新合集、Alplox 频道目录与 kakaxi 的两个列表重新下载解析，3419 个频道条目按地域范围过滤后剩 226 个候选，逐条探活后 1 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮 0 新增：

- 新增频道 1 条：国际 1 条（TVA：Nickelodeon，儿童频道）。现存 3006 条：广东 26、河南 57、香港 78、澳门 14、台湾 75、国际 2684、央视及其他省儿童频道 72，儿童频道共 105 条。同名台仍最多 2 条，无重复归一化地址。
- 跳过：不可达 7 条（kilvn 的直播与 EPG 共 3 条断连，第 9 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；aiyakuaile 的带账号密码示例地址连不上）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续九轮 403，机房 IP 被挡，留待家里测）；非直链 6 条（kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 32 条（已在库里 24 个；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：226 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），1 条通过；死链 29 条、不可达 191 条、受限 5 条未并入。kakaxi 列表里的凤凰卫视中文/资讯/香港台（phenix.php）探活未通过，未并入。TVA 的 ♥18+ 分组 116 条不进公开频道表，且全部已在本地成人文件里，0 新增；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件仍为 40668 条。

## 第十二批合并（2026-11-15 23:06，每小时整理）

本轮换用新关键词（iptv-playlist、m3u8、tvbox、live-tv、iptv、epg、free-tv、android-tv）搜 GitHub，230 个仓库里 27 个是之前没见过的新仓库，全部是 Android TV 应用/客户端（播放器、Jellyfin/Emby 客户端、去臃肿工具等），没有可直接收录的列表地址，未进正表（Gathin23/cleanyourtv 是用户永久排除项，不选）；网页搜索也未发现新列表（iptv-org 全量、Free-TV、Plex 全地区均已在库里）。常查源的 README 共抽出 36 个地址，另补 13 个，探活 17 个，通过 8 个但全部已在库里或按规则不收，播放列表/EPG/配置 0 新增；又把 TVA 自更新合集、Alplox 频道目录与 kakaxi 的两个列表重新下载解析，3419 个频道条目按地域范围过滤后剩 235 个候选，逐条探活后 9 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮 0 新增：

- 新增频道 9 条：国际 9 条（TVA：Сериал Пёс、Душевное、BBC News UK、Nat Geo Wild HD、Investigation Discovery HD、Капитан фантастика、Ужасающее HD、1+1 Україна、Спорт 4 Украина）。现存 3005 条：广东 26、河南 57、香港 78、澳门 14、台湾 75、国际 2683、央视及其他省儿童频道 72，儿童频道共 104 条。同名台仍最多 2 条，无重复归一化地址。
- 跳过：不可达 8 条（kilvn 的直播与 EPG 共 3 条断连，第 8 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；aiyakuaile 的带账号密码示例地址连不上）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续八轮 403，机房 IP 被挡，留待家里测）；非直链 6 条（kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 32 条（已在库里 24 个；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：235 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），9 条通过；死链 29 条、不可达 192 条、受限 5 条未并入。kakaxi 列表里的凤凰卫视中文/资讯/香港台（phenix.php）探活未通过，未并入。TVA 的 ♥18+ 分组 116 条不进公开频道表，且全部已在本地成人文件里，0 新增；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件仍为 40668 条。

## 第十一批合并（2026-11-15 22:06，每小时整理）

本轮原 6 个关键词搜 GitHub，129 个仓库 0 个新仓库；换用新关键词（live-tv、m3u8、tvbox、iptv-playlist）再搜，118 个仓库里 7 个是之前没见过的新仓库（dbghelp/html-iptv-player、ovosimpatico/xtream2m3u、joddude/iptvscan、afzafri/IPTV-Player-Web-App、atanuroy22/iptv、locnvbetasoft/iptv-playlist、windozalmi/Playlist_IPTV_Pribadi），其中 locnvbetasoft 的 README 列了 521 个 iptv-org 分表地址；新仓库与常查源的 README 共抽出 563 个地址，另补 13 个，探活 289 个，通过后并入播放列表 1 条、EPG 2 条；又把 TVA 自更新合集、Alplox 频道目录与 kakaxi 的两个列表重新下载解析，3419 个频道条目按地域范围过滤后剩 249 个候选，逐条探活后 14 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮 0 新增：

- 新增播放列表 1 条：dbghelp 的新加坡合集 playlist.m3u8（StarHub + mewatch 频道，带 EPG 引用）。
- 新增 EPG 播放列表 2 条：dbghelp 的新加坡 StarHub 节目单 starhub.xml 与 mewatch 节目单 mewatch.xml（实测均为真 XMLTV）。kakaxi 的 epg.xml 已在库里（https 形式），未重复收。
- 新增频道 14 条：国际 13 条（TVA：Discovery、Наука、ТВ HD、ТВТ HD、НТН HD、МТМ、Спорт 5、Охотник и рыболов、Channel 13 以色列、Суспільне Крим、Balticum 立陶宛、Твій Серіал、Хит）、儿童 1 条（Fresh Kids）。现存 2996 条：广东 26、河南 57、香港 78、澳门 14、台湾 75、国际 2674、央视及其他省儿童频道 72，儿童频道共 104 条。同名台仍最多 2 条，无重复归一化地址。
- 播放列表清理：locnvbetasoft 列出的 517 个 iptv-org 分国家/分分类/分语言地址全部不收（只留全量 index.m3u）；另按同一规则清理了库里已有的 5 条旧变体（countries/tw、countries/cn、categories/news、categories/sports、index.category.m3u），现播放列表 160 条。dbghelp 的 3 个 HTML 播放器/节目单查看页不是直链，未收。
- 修正：urlutils.normalize_url 对无方括号的 IPv6 直播地址（如移动 2409:8087 开头的运营商源）返回 None，导致合并脚本把 42 条旧移动 IPv6 地址算成一组“重复”（第九、第十批里注明的已知问题），且新 IPv6 候选会被误判为重复而跳过。已修：无方括号的 IPv6 字面量先补方括号再解析，重建 netloc 时保留方括号，末尾的 :数字 一律算地址的一部分、不拆成端口。修后重抽重探重并，重复检查为 0，无新增频道；以后新 IPv6 运营商源可正常去重并入。
- 跳过：不可达 57 条（kilvn 的直播与 EPG 共 3 条断连，第 7 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；aiyakuaile 的带账号密码示例地址连不上；其余 50 条为 iptv-org 分表变体探测失败）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续七轮 403，机房 IP 被挡，留待家里测）；非直链 232 条（iptv-org 分表变体 216 条，探活通过但按规则不收；dbghelp 的 HTML 播放器页 3 条；2 个新加坡 EPG 已改放 EPG 分组；kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件；另 5 条为本次清理掉的库里旧变体）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 287 条（iptv-org 分国家/分地区变体 251 个；已在库里 28 个，含 iptv-org 的 cn / tw / news / sports 4 条；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：249 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），14 条通过；死链 29 条、不可达 201 条、受限 5 条未并入。Alplox 的 cl / us / mx 三个分表已 404（上游撤了分表，只有 channels.m3u 还在）。kakaxi 列表里的凤凰卫视中文/资讯/香港台（phenix.php）探活未通过，未并入。TVA 的 ♥18+ 分组 116 条不进公开频道表，且全部已在本地成人文件里，0 新增；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件仍为 40668 条。

## 第十批合并（2026-11-15 21:06，每小时整理）

本轮换用新关键词（iptv、m3u、tvbox-config、free-tv、live-stream、epg-xml）搜 GitHub，129 个仓库里 23 个是之前没见过的新仓库，其中 LaQuay/TDTChannels（西班牙官方地面电视列表）、khw934/TV（TVBox 配置）等仓库的 README 共抽出 57 个地址，探活 35 个，通过 15 个后并入 EPG 2 条；又把 TVA 自更新合集（1876 条，2026-11-15 当天更新）、Alplox 频道目录与 kakaxi 的两个列表重新下载解析，3615 个频道条目按地域范围过滤后剩 291 个候选，逐条探活后 42 条新频道并入 live-channels.json；成人直播源另进本地文件，本轮 0 新增：

- 新增 EPG 播放列表 2 条：TDTChannels 的西班牙地面电视节目单 TV.xml.gz（XMLTV）和 TV.json（节目事件 JSON）。TDTChannels 的 10 条频道列表地址（tv.m3u / tv.m3u8 / tv.json 等）全部 403，机房 IP 被挡，只留待家里测，未并入。
- 新增频道 42 条：国际 41 条（TVA：乌克兰 1+1、Суспільне、Матч! 系列、Телекафе、Дорама、Food Network、Discovery Channel HD、Eurosport 1 HD 等）、儿童 1 条（NIKI KIDS）。另把库里原有的一条带 token= 的 TV Apollon（阿尔巴尼亚台，探活 403 三次，token 已过期）移到了 live-channels-invalid.json。现存 2982 条：广东 26、河南 57、港澳台 167（香港 78、澳门 14、台湾 75）、国际 2632、儿童频道 100。同名台仍最多 2 条，无重复归一化地址（合并脚本报的 41 条“重复”是已知问题：42 条旧移动 IPv6 地址归一化返回 None 被算成一组，实际各不相同，本轮未动）。
- 修正：本轮第一遍合并误把 36 条带 token= 会话参数的地址并进去了（抽取脚本在磁盘上的版本丢了 2006 轮的 token= 过滤规则；2006 轮的统计里明明有 time_signed_token_param 42 条）。已把这 36 条从 live-channels.json 删掉、恢复 token= 过滤后重新抽取探活合并，最终新增 42 条、0 条带 token=；2006 轮的抽取脚本也已补上这条过滤，避免以后再漏。
- 跳过：不可达 9 条（kilvn 的直播与 EPG 共 3 条断连，第 6 轮；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；Guovin iptv-api 的 gd/source.json 404；aiyakuaile 的带账号密码示例地址连不上）；受限 11 条（TDTChannels 10 条列表地址 403；109.233.89.170 的 Adventure_HD 单频道流连续六轮 403，机房 IP 被挡，留待家里测）；非直链 11 条（freemytv 的 apps.json 是 webOS 启动器应用清单；AerialViews 的 2 个 JSON 是屏保视频清单且走 GitHub 网页版；TDTChannels 的 2 个电台节目单不收电台；kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件）；重复 3 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml，https 形式已在库里）；未探活 35 条（已在库里 27 个；占位/示例地址 6 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：291 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），78 条通过，42 条并入（另 36 条带 token= 的已按规则排除）；死链 31 条、不可达 217 条、受限 7 条未并入。kakaxi 列表里的凤凰卫视中文/资讯/香港台（phenix.php）探活未通过，未并入。TVA 的 ♥18+ 分组 116 条不进公开频道表，且全部已在本地成人文件里，0 新增；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件仍为 40668 条。
- 网页搜索：iptv-org 的 index.m3u 与 Free-TV 各国分表已在库里；Plex 全地区列表（BuddyChewChew/app-m3u-generator 的 plex_all.m3u，2890 条）已在库里，不再重复收。

## 第九批合并（2026-11-15 20:06，每小时整理）

本轮换用新关键词（tvbox、diyp、iptv-channels、live-tv、m3u8、epg）搜 GitHub，152 个仓库里 12 个是之前没见过的新仓库，其中 10 个资源型仓库的 README 共抽出 25 个地址，另从常查源与网页搜索补了 48 个，探活 34 个，20 个通过后并入（播放列表 5 条）；又从新播放列表里抽出 3615 个频道条目，按地域范围过滤后剩 648 个候选，逐条探活后 366 条新频道并入 live-channels.json；成人直播源另进本地文件，共新增 91 条（只留本地，不上传）：

- 新增播放列表 5 条（乌克兰 TVA 自更新合集 avto-iptv-tva.m3u，1770 条频道，2026-11-15 当天更新；Alplox 的西班牙语频道目录 channels.m3u 及智利/美国/墨西哥分表 cl / us / mx 共 4 条）。
- 新增频道 366 条：国际 363 条（TVA 348 条——乌克兰、俄罗斯及欧洲各国频道、电影、体育、儿童；Alplox 18 条——智利 CNN Chile、ITV Patagonia、DW 西班牙语、BBC News 阿拉伯语、CNN-News18、WION、Bloomberg 欧洲/美国等）、央视及其他省儿童频道 3 条（华数少儿动画等）。同名台仍最多 2 条，无重复归一化地址（合并脚本报的 41 条“重复”是已知问题：42 条旧移动 IPv6 地址归一化返回 None 被算成一组，实际各不相同，本轮未动）。现存 2941 条：广东 26、河南 57、港澳台 167、国际 2621、央视及其他省儿童频道 70。
- 跳过：不可达 10 条（dearbulut 的 EPG 404；istiakrahman15 的 iptv.json 404；NasiLemakk 的 plutotv_us.m3u 404；kilvn 的直播与 EPG 共 3 条断连；e.erw.cc 的 all.xml.gz；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404；aiyakuaile 的带账号密码示例地址连不上）；受限 2 条（109.233.89.170 的 Adventure_HD 单频道流连续五轮 403，机房 IP 被挡，留待家里测；Gitee 的 myepg 403，Gitee 防盗链）；非直链 13 条（Alplox 的 channels.json 是 channels.m3u 的 JSON 版、3 个 CDN 镜像与之一样只留 raw 直链；flagcdn 的 codes.json 只是国旗代码数据；kakaxi 的 ipv6.m3u 是空表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的 tw.txt 是 2016 年旧表；3 个成人播放列表只进本地文件；占位地址 1 个）；重复 4 条（kakaxi 的 ipv4.txt / iptv.txt / epg.xml 与 myEPG 的 epg.xml 已在库里）；未探活 39 条（已在库里 29 个；占位/示例地址 8 个；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：648 个候选频道用单次快速探针（读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），366 条通过；死链 28 条、不可达 249 条、受限 5 条未并入。带 token= 会话参数的地址（如 TVA 里 42 条 teledom / uplink 域名流）一律不并入（token 会过期，不是长期可用地址）；TVA 的 ♥18+ 分组 116 条不进公开频道表，其中 91 条新地址进了本地成人文件；TVA 的 TEST-1、Ott Club 等测试/VPN 分组大多探活失败，未并入。Alplox 的 cl / us / mx 分表与 channels.m3u 内容大量重复，本轮 0 条新频道来自这三个分表。
- 成人直播（本地文件，不上传）：TVA 的 ♥18+ 分组新增 91 条；4 个已知成人播放列表（dzh0ni、m3u.cl、yuanxin69 guowai、TCatCloud）重解析 0 新增，本地成人文件现为 40668 条。

## 第八批合并（2026-11-15 17:06，每小时整理）

本轮新增播放列表 15 条、EPG 播放列表 4 个、TVBox 配置 2 个；成人直播源另进本地文件，共新增 83 条（只留本地，不上传）：

- 新增：播放列表 15 条（judy-gotv 的 ofiii / 4gtv / litv / MytvSuper-Ts / logo-smart / smart 6 条；suxuang 的 myIPTV IPv4 / IPv6 / 移动 IPv6 3 条；956065487 的 myzhiboyuanPro / myzhiboyuan-tx 2 条；kakaxi 的 ipv4.txt / iptv.txt 2 条；BuddyChewChew 的 Plex 全量 plex_all.m3u；zilong7728 的 best_sorted.m3u）、EPG 播放列表 4 个（myhomebox 的 4g / ofiii；51zmt 的 e.xml.gz；kakaxi 的 epg.xml）、TVBox 配置 2 个（956065487 的 interface.txt、0821.json）。
- 跳过：不可达 8 条（kilvn 的 iptv.m3u 与两个 EPG 地址；erw 的 all.xml；judy-gotv 的 MytvSuper.m3u 与 beesports.m3u；百度 easy_tv_live；epg.iill.top）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流 403）；非直链 6 条（kakaxi 的 ipv6.m3u 是空列表；suxuang 的移动 IPTV.m3u 无 #EXTM3U 头；yuanxin69 的台湾列表是 2016 年旧版；3 个成人播放列表只进本地文件）。
- 成人直播（本地文件，不上传）：本地成人文件现为 40577 条。

## 第八批合并（2026-11-15 17:06，每小时整理）

本轮换用新关键词（iptv、m3u、tv-live、zhiboyuan、live-stream、epg-xml）搜 GitHub，123 个仓库里 70 个是之前没见过的新仓库，其中 21 个资源型仓库的 README 共抽出 41 个地址，另从仓库文件树和网页搜索补了 14 个，探活 36 个，通过 24 个后并入（播放列表 15 条、EPG 播放列表 4 个、TVBox 配置 2 个）；又从新播放列表里抽出 5748 个频道条目，按地域范围过滤后剩 631 个候选，逐条探活后 37 条新频道并入 live-channels.json；成人直播源另进本地文件，共新增 83 条（只留本地，不上传）：

- 新增播放列表 15 条（zilong7728 的每日更新 best_sorted.m3u；judy-gotv 的台湾/香港专辑 ofiii / 4gtv / litv / MytvSuper-Ts / smart / logo-smart 共 6 条；kakaxi 的每日更新 ipv4.txt / iptv.txt；suxuang 的 ipv4.m3u / ipv6.m3u / 移动IPV6.txt；956065487 的 myzhiboyuanPro.m3u / myzhiboyuan-tx.txt；BuddyChewChew 的 Plex 全量 plex_all.m3u）、EPG 播放列表 4 个（51zmt 的 e.xml.gz、kakaxi 的 epg.xml、myhomebox 的 4g.xml / ofiii.xml）、TVBox 配置 2 个（956065487 的 0821.json / interface.txt，其中 interface.txt 是配置索引）。
- 新增频道 37 条：港澳台 27 条（凤凰卫视台/香港台/资讯台、翡翠台 1080P 与备用线、TVB 娱乐新闻台、无线新闻台、RTHK31、VIUTV、澳视澳门/澳视卫星、Astro AOD、AMC电影台、亚洲武侠、东森财经新闻、民视新闻HD、华视HD、纬来精采、寰宇新闻台、南国都市、韩国电影 1/2 等，多为 jdshipin 中继线）、广东 1 条（广东民生）、国际 5 条（ABC News Live、Bloomberg Asia、CBC News、CNA、RT Doc 俄语纪录）、儿童 2 条（河北少儿、韩国 EBS 少儿）。同名台仍最多 2 条，无重复归一化地址。现存 2575 条：广东 26、河南 57、港澳台 167、国际 2258、央视及其他省儿童频道 67（央视 2、其他省 65）。
- 跳过：不可达 8 条（kilvn 的直播与 EPG 共 4 条，服务器断连；e.erw.cc 的 all.xml.gz；epg.iill.top 的 epg.xml；judy-gotv 的 MytvSuper.m3u / beesports.m3u 为 404）；受限 1 条（109.233.89.170 的 Adventure_HD 单频道流连续两轮 403，机房 IP 被挡，留待家里测）；非直链 6 条（yuanxin69 的 tw.txt 是 2016 年旧表，抽查 kylintv 流已死；guowai.m3u 与两个成人播放列表只进本地文件；suxuang 的移动IPTV.m3u 没有 #EXTM3U 头；kakaxi 的 ipv6.m3u 是空表，只有表头）；未探活 20 条（占位/示例地址 8 个；已在库里 8 个；iptv-org 的分国家/分语言变体 2 个，只留全量；best_sorted.m3u8 与 .m3u 同文件 1 个；电台列表 1 个）。
- 频道探活说明：631 个候选频道先用 3 次流探针跑了 38 分钟，因运行环境重启而中断且无任何结果落盘；改用单次快速探针重跑（每个地址 1 次、读前 3000 字节认 #EXTM3U，失败只算“本轮不收”不判死链），8 分钟完成 714 条记录，57 条通过。judy-gotv 的 7 个中继域名（smt.goiptv.us.ci、smt.passwdword.xyz、aktv-stream.m16tv.cfd、caonizuzong.cc.cd、clawcloud.goiptv.de5.net、edgeone.passwdword.xyz、litv.zapi.us.kg）共 442 条全部超时或断连，机房 IP 疑似被挡或中继已死，其频道线未并入；但 6 条 judy 播放列表地址本身已入库，用户可在家里直接试。带 txSecret/txTime 签名的地址（如南国都市、梨园）一律不并入（签名会过期）；复查时又去掉 1 条“龙门飞甲”（单个电影点播标题，不是频道）。
- 成人直播（本地文件，不上传）：dzh0ni 的 iPTV-Free-List_XXX.m3u 新增 38 条、m3u.cl 的 XXX.m3u 新增 27 条、yuanxin69 的 guowai.m3u 新增 18 条，本地成人文件现为 40577 条。
- 已知问题：库里 42 条旧移动 IPv6 地址写的是无方括号形式（如 http://2409:8087:2001:20:.../ott.mobaibox.com/...），normalize_url 对这类地址返回 None，计重检查会把它们算成一组“重复”，实际 42 条地址各不相同、此前已在库里，本轮未动；后续如需清理再单独处理。

## 第七批合并（2026-11-15 16:06，每小时整理）

本轮换用新关键词（m3u8、tvbox、epg、live-tv、diyp、zhibo）搜 GitHub，39 个新仓库里 21 个资源型仓库的 README 共抽出 83 个地址，另从网页搜索补了 9 个，探活 62 个，30 个通过后并入（播放列表 16 条、EPG 播放列表 13 个、TVBox 配置 1 个）；成人直播源另进本地文件，共新增 30 条（只留本地，不上传）：

- 新增：播放列表 16 条（Pluto TV 全量 pluto_all.m3u；BuddyChewChew 的 LocalNow / Xumo / LG 美国 / TCL / 体育赛事直播 5 条；Guovin iptv-api 的 gd 全量、IPv6、IPv4 三个每日更新列表；范明明 zhiboyuan 的 fanmingming.m3u 与 DIYP 版、ff.txt；TCatCloud 的 IPTV.m3u；reysc 的 ntPlayer 全量 txt；mayaxcn 的 tv.txt；iptv-org 的按分类索引 index.category.m3u）、EPG 播放列表 13 个（taksssss 的 51zmte1 / 51zmte2 / erw / epgpw 中国/香港/台湾 6 个；litiande03 的 pl.xml.gz；zzq1234567890 的 swepg / twepg；Pluto TV 的 all.xml.gz；LocalNow 的 epg.xml；范明明 e.xml；mytv-android 的 myEPG 输出 epg.xml）、TVBox 配置 1 个（tv.cvkkj.top 的 1.json，带注释头，含 spider）。
- 跳过：死链 3 条（xiaolvdouya/live 的 fanmingming.m3u、fanmingming 2.m3u、Moexin 的 IPTV.m3u 均为 404）；不可达 5 条（Guovin 的 source.json 404；sinovision 直播流、qiaoji8 配置、erw 的 all.xml、izbds 的 iptv4.txt 均连不上）；受限 2 条（109.233.89.170 的 Adventure_HD 单频道流 403，机房 IP 被挡；Gitee 的 myepg 403，Gitee 防盗链）；非直链 11 条（zzq1234567890 的繁简体电视台目录只是频道名清单、没有地址；3 个成人播放列表只进本地文件；hebijunge 的 6 个 ghproxy 镜像与 raw 文件重复）；未探活 30 条（示例/占位地址 2 个；Pluto 的 15 个分国家变体，只留全量 1 个；hebijunge 的 jsdelivr / releases 镜像 6 个；ghproxy 镜像 4 个；litiande03 的 github.com/raw 重复 1 个；Guovin 的 jsdelivr 重复 2 个）。
- 探活误判修正：FRANKASEE 与 TCatCloud 的 Adult.m3u 探针报不可达，实际 curl 取回 200 且是有效 M3U（文件没有 #EXTM3U 头，直接以 #EXTINF 开头，探针只认 #EXTM3U 头会漏掉）；pluto_all.m3u 三次探测 1 次失败，curl 复查 200 且内容正常，按通过计。zzq1234567890 的两个中文文件名 txt 探针报编码错，百分号编码后 curl 取回 200，但内容只是频道名清单，已按非直链跳过。
- 其余新仓库多为播放器、工具和推流脚本（Apple TV 应用、Kodi 插件、m3u8 下载器、无人直播推流、EPG 工具等），没有可直接收录的列表地址，未进正表。
- 成人直播（本地文件，不上传）：FRANKASEE/tviptv 的 Adult.m3u 新增 24 条、TCatCloud 的 Adult.m3u 新增 1 条（其余 24 条与前者重复）、AzeemHadzrie 的 Playboy.m3u 新增 5 条（其余 23 条已在库里），本地成人文件现为 40494 条。

## 第六批合并（2026-11-15 15:06，每小时整理）

本轮换用新关键词（iptv m3u8、tvbox json、epg guide、live tv playlist、m3u channels、diyp tv）搜 GitHub，43 个新仓库里 22 个资源型仓库的 README 共抽出 24 个地址，另从 amazeyourself/m3u 的仓库树补了 34 个（31 个南亚供应商列表 + Plex / PlutoTV / SamsungTVPlus 3 个全量列表），探活 52 个，48 个通过后并入：

- 新增：播放列表 45 条（南亚供应商合集 34 条：amazeyourself 的 dishd2h / jtv / akashgo 等 31 个供应商列表 + Plex / PlutoTV / SamsungTVPlus 三个全量列表；意大利 tvit 与 OpenIPTVItaly 的 3 条；德国 german-tv.m3u；印尼 world_ip_tv；dearbulut 的 best / online / index 三个 3.9 万频道索引；孟加拉 Ip-tv-Collection 的 ACTIVE / GEO / COMPLETE 三个合集）、EPG 播放列表 3 个（意大利 tvit 的 list.xml 与 JSON 版 list.json、Ip-tv-Collection 的 epg.json——后两个是 JSON 格式节目单，不是 XMLTV）。
- 跳过：不可达 2 条（dearbulut 的 epg/guide.xml.gz 404；Gitee 的 chuanshuo.json 返回 423，Gitee 防盗链挡了机房 IP）；非直链 2 条（安徽联通的 m3u8 里全是 10.x 内网地址，需联通内网；tvit 的 list.json 是频道索引数据接口，不是 TVBox 配置）；未探活 44 条（示例/占位地址 7 个；amazeyourself 的 34 个分国家变体，只留了 3 个全量列表；kodi21 文件夹与根目录重复的 2 个；yinghezhinan 的 top98.json 已在配置库里）。
- 其余新仓库多为播放器、EPG 工具和解析库（印度 IPTV 应用、Pluto for Channels、Rakuten 生成器等），没有可直接收录的列表地址，未进正表。

## 第五批合并（2026-11-15 14:06，每小时整理）

本轮换用新关键词（epg xmltv、iptv playlist、tvbox config、diyp m3u、live stream m3u、m3u8 tv）搜 GitHub，47 个新仓库里 22 个资源型仓库的 README 共抽出 68 个地址，另从两个无标准 README 的仓库（IPTV-Scraper-Zilla、Mrgify-BDIX-IPTV，README 文件名是 Readme.md）补了 6 个，探活 36 个，24 个通过后并入：

- 新增：EPG 播放列表 6 个（北京联通嗅探的 epg.xml、Pluto TV 全量 all.xml、泰国 iptv36 的 epg.xml、tvapp2 的 zap2it 频道 xmltv.1.xml、IPTV-Scraper-Zilla 的 tubi_epg.xml / xumo_epg.xml.gz）、播放列表 10 条（俄罗斯 ngrch 的 ru / music / cartoons 三个 M3U、泰国 iptv36 的 v1 / v2、大嘴 TV 每日更新的 iptv.m3u / iptv-ok.m3u、IPTV-Scraper-Zilla 的 combined-playlist / tubi / xumo 三个合集）、TVBox 配置 8 个（hebijunge 每日合并的 tvbox_recommended / tvbox / healthy / vod / live / short 六个变体、FanchangWang 的多仓 tvbox.json / my.json）。
- 跳过：死链 1 条（NasiLemakk 的 plutotv_us.m3u 404）；不可达 1 条（Mrgify-BDIX-IPTV 的 playlist.m3u 三次探测都读不到内容）；非直链 10 条（北京联通的 7 个 M3U 全是 rtp 组播或经 iptv.local:8080 本地代理，需联通内网；两个 playlist JSON 是嗅探工具的原始频道数据，不是 TVBox 配置；epg.xml.gz 与同仓库 epg.xml 内容相同）；未探活 38 条（本机/内网/占位地址 22 个、同一文件的 ghproxy/jsdelivr/releases 镜像变体 16 个，只探了 raw 直链）。
- 其余新仓库多为工具或播放器（M3U 下载器、播放列表管理器、EPG 生成器、JioTV 等），没有可直接收录的列表地址，未进正表。

## 第四批合并（2026-11-15 13:06，每小时整理）

本轮换用新关键词（diyp、iptv m3u、tvbox、xmltv、mytv、live tv m3u8）搜 GitHub，40 个新仓库里 7 个资源型仓库的 README 共抽出 23 个地址，加上网页搜索找到的 6 个，探活 25 个，13 个通过后并入：

- 新增：EPG 播放列表 6 个（印尼 dhanytv 的 epg.xml、瑞士 TV7 的 tv7_epg / teleboy / init7 三份 gz、日本 JapanTV 的 guide.xml、epg.pw 中国区未压缩版 epg_CN.xml）、播放列表 4 条（lemonTV 的 iptv-fe.m3u、印尼 dhanytv / dhanytv-ott 两个 M3U、YouTube 直播合集 youtube.m3u）、TVBox 配置 1 个（kukuqi666/TVboxOSC 的 R18.json）。
- 跳过：死链 1 条（init7 的 SRG 播放列表 404）；不可达 11 条（广东移动抓取脚本里的运营商内网地址 7 个、ERW 的 e.xml / cc.xml / allcc.xml 3 个、yinghezhinan 的 tv.xn--yhqu5zs87a.top 返回 520）；非直链 6 条（jihulab 的 ymshaoer 实际是 PNG 图片、init7 的 tvchannels.m3u 是 UDP 组播地址需瑞士 Init7 内网、带 AuthInfo=xxx 占位符的示例地址与 host:5523 模板地址等）；重复 0 条。
- 其余新仓库多为工具或解析库（播放器、EPG 生成器、M3U 管理器、抓取脚本），没有可直接收录的列表地址，未进正表。

## 第三批合并（2026-11-15 12:06，每小时整理）

本轮换用新关键词（epg、m3u8、iptv china、tvbox json、直播源、影视）搜 GitHub，30 个新仓库里 14 个资源型仓库的 README 共抽出 19 个地址，探活 11 个通过后并入：

- 新增：EPG 播放列表 7 个（suzukua/epg 的 t.xml，EPGTalk 的 guide.xml 官网 + raw 双地址，英国 Freeview EPG，spark 的 pp.xml，西班牙 dobleM 的 guiatv.xml / guiaiptv.xml）、播放列表 4 条（Plex 美国频道 plex_us.m3u、huangsuming 的央视卫视 tvlist.txt 与电台 radio.txt——内容实为 M3U、上海联通 IPTV 的 IPTV_Enhanced_change.m3u，经 gh-proxy 直连）。
- 跳过：8 条候选未进正表——示例地址 1 个（example.com）、本机地址 3 个（localhost）、占位文件名 1 个（FILENAME.m3u）、GitHub 网页版 txt 日志 3 个（非直链）；死链/受限 0 条；重复 0 条。
- 其余新仓库多为工具或解析库（m3u8 解析器、EPG 生成器、播放器壳），没有可直接收录的列表地址，未进正表。

## 第二批合并（2026-11-15）

两批全网搜索的新发现（`new-finds.json` 288 条、`new-methods-finds.json` 37 条）按技能方法探活、去重后并入：

- 新增：TVBox 配置 51 个、播放列表 65 条（M3U 39、M3U8 18、TXT 8）、EPG 播放列表 13 个、DIYP 接口 1 个、台标模板 1 个（范明明 `https://live.fanmingming.cn/tv/{name}.png`）、CMS 节点 1 个（空壳影视默认源）。
- 直播频道没有新增：第一批里标为 stream 的 57 条其实全是播放列表文件，不是单个频道，所以并进了 `live-lines.json` 的 playlists 分组，没有进直播频道。
- 跳过：已在库里的重复 6 条（另有 8 条是第一批自带的 already_in_harvest 标记，逐一核对确认都在库里）；死链/不可达 92 条；受限（401/403/429，机房 IP 被挡）12 条未进正表；HTML 落地页 3 个（摸鱼儿、饭太硬、宝盒）不是直链，未进；59 个 GitHub 仓库和 1 个 APK 只是发现线索，不是直接可用的资源，未进；少儿频道（`http://xhztv.top/xhz`）已在追剧资源里，不再重复收进配置。
- 探活误判：7 个标为 reachable 的配置实际不可用——5 个 gh.con.sh 代理返回停用页（suspent.txt）、1 个跳转到域名停放页（julydns.com）、1 个跳转回网站首页，全部排除；只认状态码会漏掉这类情况，以后探活要同时看跳转后的最终地址。
- .txt 文件按内容重分：live.txt、live_lite.txt、others.txt、Tivi.txt、zby.txt 是频道列表，进播放列表；tvbox.txt、dm.txt 是配置文本，进配置。
- 注意：51zmt 的 e.xml 和 cc.xml 跳转后是同一个文件；两个 Gitee 镜像地址带 signature 参数，可能过期；范明明台标库站根 404，但 tv/*.png、e.xml、tv/m3u/*.m3u 子路径都可直连。

## 怎么用

- **TVBox / 影视仓**：在软件里填 `configs/config-files.json` 中任一配置的 `raw_url`（或 `mirror_url`），即可加载整份配置。配置里已经包含点播源和直播线路。
- **直播列表**：`live/live-channels.json` 是一条地址一条频道的清单，每条带频道名、地址、分组、国家、台标、`tvg-id` 和来源。`sources` 字段说明这条地址都出现在哪几个原始文件里，`names` 列出见过的所有频道名。`live/live-lines.json` 里新增的 `playlists` 分组是探活通过的 M3U/TXT 播放列表地址（170 条），可直接订阅或导入播放器；`lines` 仍是 TVBox 配置里的 lives 项。
- **点播源**：`vod/vod-sources.json` 是 TVBox 配置里的 `sites` 项，每条带 `key`、`name`、`type`（0=CMS、1=XPath、3=爬虫）、`api`、`ext` 和搜索/筛选标志，`configs` 说明它出自哪几份配置。
- **节目单**：`epg/epg-sources.json` 里有 EPG 地址模板（`{name}`、`{date}` 占位符）、频道用的 `tvg-id` 清单和 169 个 EPG 播放列表地址，另有 1 个 DIYP 接口端点和 1 个台标模板（范明明 `https://live.fanmingming.cn/tv/{name}.png`）。播放列表头写 `x-tvg-url`，频道按 `tvg-id` 匹配节目单。
- **追剧资源**：`guides/zhuiju-resources.json` 每条带分类、五维评分（资源多、速度、干净、稳定、易用）、四维风险（版权、安全、隐私、支付）和验证记录。

## 数据来源

- [ciweihaha/tvbox](https://github.com/ciweihaha/tvbox)（fork 自 qist/tvbox）：TVBox 配置、点播源、直播列表。
- [ciweihaha/awesome-zhuiju-free](https://github.com/ciweihaha/awesome-zhuiju-free)（fork 自 laoma528/awesome-zhuiju-free）：追剧资源清单。
- [ciweihaha/IPTV](https://github.com/ciweihaha/IPTV)（fork 自 Free-TV/IPTV）：各国频道表和总播放列表。

## 整理方法

- **归一化**：地址去首尾空格，协议和域名小写，去掉默认端口（80/443），去掉无意义的尾部斜杠，去掉 fragment；查询参数保留（带 token 的流地址不能丢）。
- **去重**：同一个归一化地址只保留一条，来源记在 `sources` / `configs` 里。去重前 57253 条，去重后 51672 条，合并了直播频道 5100 条、点播源 462 条、直播线路 10 条、追剧资源 1 条。
- **清理**：去掉空地址、格式错误、带空格、缺协议头的地址共 212 条，去掉缺地址或地址无效的直播线路 4 条。127.0.0.1、localhost、10/172.16/192.168 内网地址直接清理（本机地址放进公开列表没有意义）。
- **分类**：直播、点播源、配置地址、追剧资源、EPG 分开存放；失效频道单独放 `live/live-channels-invalid.json` 留着复查；成人内容（分组名“性视界”，来自 listx.m3u / livex.m3u，共 40668 条）只放在本地文件 `live/live-channels-adult.json`，不混进正常列表，也不上传到本仓库。

## 注意

- 这些地址大多是第三方收集来的，稳定性和版权都不如自有源，只适合做补充参考，不适合替换自有链路。
- 直播频道建议先按“3 次探测、6 档状态”的方法探活后再用（失效的不直接删，复查活了再移回来）。
- 本仓库只做整理，不生产流；上游源失效、改版是常态，数据会随时间过期。
