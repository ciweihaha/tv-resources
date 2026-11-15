# tv-resources

电视直播、点播源、TVBox 配置和追剧资源的整理合集。数据来自下面三个仓库的公开内容，经过去重和清理后按分类存放。整理时间：2026-11-15。

## 文件一览

| 文件 | 内容 | 条数 |
|---|---|---|
| live/live-channels.json | 直播频道（电视 + 电台，正常内容，已去重；国内只留广东/河南/香港/澳门/台湾的省一级频道，深圳/东莞市台例外保留，国际不限；同名台最多留 2 条；不含购物/广告台、景区直播） | 2471 |
| live/live-channels-invalid.json | 标记为失效的频道，留着复查，不用于播放 | 303 |
| live/live-lines.json | 直播线路（TVBox 配置里的 lives 项，带 EPG/台标模板）+ 播放列表（全网搜索探活通过的 M3U/TXT 列表地址） | 37 条线路，144 条播放列表 |
| vod/vod-sources.json | TVBox 点播源（sites，去重后） | 797 |
| configs/config-files.json | TVBox 配置文件地址（raw + 镜像）与 spider 引擎、CMS 节点 | 74 个配置，8 个 spider，1 个 CMS 节点 |
| epg/epg-sources.json | EPG 模板、EPG id、EPG 播放列表地址、DIYP 接口、台标模板 | 3 个模板，1853 个 id，149 个列表，1 个 DIYP 接口，1 个台标模板 |
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
- **直播列表**：`live/live-channels.json` 是一条地址一条频道的清单，每条带频道名、地址、分组、国家、台标、`tvg-id` 和来源。`sources` 字段说明这条地址都出现在哪几个原始文件里，`names` 列出见过的所有频道名。`live/live-lines.json` 里新增的 `playlists` 分组是探活通过的 M3U/TXT 播放列表地址（144 条），可直接订阅或导入播放器；`lines` 仍是 TVBox 配置里的 lives 项。
- **点播源**：`vod/vod-sources.json` 是 TVBox 配置里的 `sites` 项，每条带 `key`、`name`、`type`（0=CMS、1=XPath、3=爬虫）、`api`、`ext` 和搜索/筛选标志，`configs` 说明它出自哪几份配置。
- **节目单**：`epg/epg-sources.json` 里有 EPG 地址模板（`{name}`、`{date}` 占位符）、频道用的 `tvg-id` 清单和 149 个 EPG 播放列表地址，另有 1 个 DIYP 接口端点和 1 个台标模板（范明明 `https://live.fanmingming.cn/tv/{name}.png`）。播放列表头写 `x-tvg-url`，频道按 `tvg-id` 匹配节目单。
- **追剧资源**：`guides/zhuiju-resources.json` 每条带分类、五维评分（资源多、速度、干净、稳定、易用）、四维风险（版权、安全、隐私、支付）和验证记录。

## 数据来源

- [ciweihaha/tvbox](https://github.com/ciweihaha/tvbox)（fork 自 qist/tvbox）：TVBox 配置、点播源、直播列表。
- [ciweihaha/awesome-zhuiju-free](https://github.com/ciweihaha/awesome-zhuiju-free)（fork 自 laoma528/awesome-zhuiju-free）：追剧资源清单。
- [ciweihaha/IPTV](https://github.com/ciweihaha/IPTV)（fork 自 Free-TV/IPTV）：各国频道表和总播放列表。

## 整理方法

- **归一化**：地址去首尾空格，协议和域名小写，去掉默认端口（80/443），去掉无意义的尾部斜杠，去掉 fragment；查询参数保留（带 token 的流地址不能丢）。
- **去重**：同一个归一化地址只保留一条，来源记在 `sources` / `configs` 里。去重前 57253 条，去重后 51672 条，合并了直播频道 5100 条、点播源 462 条、直播线路 10 条、追剧资源 1 条。
- **清理**：去掉空地址、格式错误、带空格、缺协议头的地址共 212 条，去掉缺地址或地址无效的直播线路 4 条。127.0.0.1、localhost、10/172.16/192.168 内网地址直接清理（本机地址放进公开列表没有意义）。
- **分类**：直播、点播源、配置地址、追剧资源、EPG 分开存放；失效频道单独放 `live/live-channels-invalid.json` 留着复查；成人内容（分组名“性视界”，来自 listx.m3u / livex.m3u，共 40494 条）只放在本地文件 `live/live-channels-adult.json`，不混进正常列表，也不上传到本仓库。

## 注意

- 这些地址大多是第三方收集来的，稳定性和版权都不如自有源，只适合做补充参考，不适合替换自有链路。
- 直播频道建议先按“3 次探测、6 档状态”的方法探活后再用（失效的不直接删，复查活了再移回来）。
- 本仓库只做整理，不生产流；上游源失效、改版是常态，数据会随时间过期。
