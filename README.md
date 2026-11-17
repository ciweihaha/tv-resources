# tv-resources

电视直播、点播源、TVBox 配置和追剧资源的整理合集。数据来自下面三个仓库的公开内容，经过去重和清理后按分类存放。整理时间：2026-11-17。

## 文件一览

| 文件 | 内容 | 条数 |
|---|---|---|
| live/live-channels.json | 直播频道（电视 + 电台，正常内容，已去重；国内只留广东/河南/香港/澳门/台湾的省一级频道，深圳/东莞市台例外保留，儿童频道不限地域，国际不限；同名台最多留 2 条；不含购物/广告台、景区直播） | 3911 |
| live/live-channels-invalid.json | 标记为失效的频道，留着复查，不用于播放 | 304 |
| live/live-lines.json | 直播线路（TVBox 配置里的 lives 项，带 EPG/台标模板）+ 播放列表（全网搜索探活通过的 M3U/TXT 列表地址） | 37 条线路，170 条播放列表 |
| vod/vod-sources.json | TVBox 点播源（sites，去重后） | 18349 |
| configs/config-files.json | TVBox 配置文件地址（raw + 镜像）与 spider 引擎、CMS 节点 | 820 个配置，231 个 spider，1 个 CMS 节点 |
| epg/epg-sources.json | EPG 模板、EPG id、EPG 播放列表地址、DIYP 接口、台标模板 | 3 个模板，1853 个 id，169 个列表，1 个 DIYP 接口，1 个台标模板 |
| guides/zhuiju-resources.json | 追剧资源（分类、评分、风险、验证记录） | 127 |

## 第四十九批合并（2026-11-17 22:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（136 个仓库，对照累计已见 880 个仓库有 9 个真正新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily latest/online/fastest 三份数据与 21:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 21:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表与 360doc 教程：除 4 个死链外均已在库）。新发现中：mnyuer/tvbox-manager（每日自动更新：multi.json 多仓指针 2 个地址、multi-cn.json 多仓指针 11 个地址、multi-ghproxy.json 多仓指针 11 个地址；clean 0821.json 86 站、jsm.json 163 站；clean_cn 0707.json 多仓指针 6 个地址、0821.json 86 站、0826.json 54 站、0827.json 33 站、XYQ.json 49 站、fty.json 48 站、js.json 298 站、jsm.json 164 站、jundie.json 24 站、mo_yu_er.json 75 站、xiaosa.json 122 站）、hanzhu340-88/tvbox（best.json 皮蛋精选 7 站、index.json 多仓指针 8 个地址）、ichbinyytak/tvbox-source（my_box.json 98 站、new.json 48 站；source/ 下 12 份：eyh.json 31 站、feimao.json 41 站、fty.json 49 站、moyu.json 111 站、moyu4k.json 111 站、nanfeng.json 93 站、niu2.json 100 站、ok.json 101 站、pg.json 87 站、tvboxorg.json 160 站、wex.json 100 站、xiaosa.json 117 站）、wolf2021/tvbox（爱优腾.json 7 站、戏曲音乐/api.json 8 站）；其余新发现无源可收：xyu3032-commits/Anikumo 是动漫漫画小说影视四合一 Flutter 应用、Mrbotrx/Tvbox_KB 的 kb_tv.m3u、vip.m3u8 与 output/channels.json 都是直播（按 VOD-only 规则不收）、dushuboy/tvbox-live 是直播流、1073140428/tvbox-ios 是 iOS 采集站应用源码、zhishixuebao-0791/Open-TV 是 Android 播放器应用且不提供源：

- 新增点播源 106 条：CMS 接口 0 条；配置内站点 106 条（ok.json 72 条、pg.json 13 条、mo_yu_er.json 11 条、爱优腾.json 5 条、xiaosa.json 3 条、feimao.json 2 条）。另有 961 条已有点播源补记了新出现的配置文件名；新增 spider 记录 10 条（jundie.json、mo_yu_er.json、my_box.json、new.json、eyh.json、moyu4k.json、nanfeng.json、niu2.json、pg.json、tvboxorg.json 的 spider；0821/jsm/fty/xiaosa/feimao/moyu/ok 等同名文件在多仓库出现，spider 归属不唯一故不记）。现存 18349 条。
- 新增 TVBox 配置 34 个：mnyuer multi.json、multi-cn.json、multi-ghproxy.json（多仓指针，只立条）、clean 0821.json、jsm.json、clean_cn 0707.json（多仓指针，只立条）、0821.json、0826.json、0827.json、XYQ.json、fty.json、js.json、jsm.json、jundie.json、mo_yu_er.json、xiaosa.json，hanzhu best.json、index.json（多仓指针，只立条），ichbinyytak my_box.json、new.json、source/ 下 eyh.json、feimao.json、fty.json、moyu.json、moyu4k.json、nanfeng.json、niu2.json、ok.json、pg.json、tvboxorg.json、wex.json、xiaosa.json，wolf2021 爱优腾.json、戏曲音乐/api.json。现存 820 个，spider 231 个。
- 成人内容清理：pg.json 87 站里 29 个成人名站点只跳过本站、不立整份；并入时跳过成人名站点 96 条、成人 host 站点 12 条、成人 api 5 条、成人 URL 2 条；合并后复核新增的 106 条全部干净。
- 跳过：探活 38 个配置地址，34 个存活、4 个死链（0725.json 与 qiaoji8 tvbox.json 连接被关闭、半糖仙人 gitee 返回 423、wya6 yc.json 返回 456）；并入时跳过 1603 条已在库、376 条相对地址 api、263 条相对地址 ext、8 条无 api。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十八批合并（2026-11-17 21:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（132 个仓库，对照累计已见 867 个仓库有 13 个真正新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily latest/online/fastest 三份数据与 20:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 20:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表：仅 2 个库外地址，且当天已有不良 verdict——yc.wya6.cn/wykj.php 13:06 死链、tv.xn--yhqu5zs87a.top 15:06 是 HTML 落地页，本轮不再重探）。新发现中：haonanren118/tvbox-kstore（source.json 多仓指针 4 个地址；custom_sources.json 是裸列表非配置，未收）、lsx9988/my-tvbox-cfg（每日自动聚合：tvbox_new.json 689 站、tvbox_lite.json 前 80 站、sites.json 纯点播 689 站、多仓订阅.json 7 个地址）、NoviceDai/PrivateTvbox（TvboxDuoChang.json 多仓指针 13 个地址、tvboxconfig.json 33 站）、szyshr199312/tvbox（best.json 111 站、lite.json 11 站）、cygoy/tvbox（api.json 3 站、api2.json 36 站、list.txt 与 url.txt 各是 1 个地址的多仓指针；225.json 是 CMS 接口返回样例，非配置，未收）、nzsm/tvbox-server（tvbox.json 154 站、XC.json 84 站、ygbox.json 179 站、tvbox_merged.json 249 站；nzsm.json 599 站里 325 个成人名，多半成人，整份不立条）、zhengqingxue/tvbox-spider（筛选/ 下 10 份是 CMS 分类筛选定义，非 TVBox 配置，未收；影视/ 下是单个 drpy 规则文件，含成人区，未收）；其余新发现无源可收：omkarcloud 的 kick/twitch-scraper 是直播流爬虫、toonflow-skills 是 AI 影视创作技能包、MercuryHub 是影视导航站、blog-cms-platform 是博客 CMS、fierabraz/tvbox-store 是 APK 商店目录：

- 新增点播源 406 条：CMS 接口 0 条；配置内站点 406 条（tvbox_new.json 253 条、ygbox.json 105 条、tvbox_merged.json 19 条、api2.json 15 条、tvboxconfig.json 7 条、XC.json 4 条、api.json 2 条、tvbox.json 1 条）。另有 1409 条已有点播源补记了新出现的配置文件名；新增 spider 记录 4 条（tvbox_lite.json、api2.json、ygbox.json、tvbox_merged.json 的 spider）。现存 18243 条。
- 新增 TVBox 配置 17 个：haonanren118 source.json（多仓指针，只立条）、lsx9988 tvbox_new.json（jsDelivr 记为镜像）、tvbox_lite.json、sites.json、多仓订阅.json（多仓指针，只立条）、NoviceDai TvboxDuoChang.json（多仓指针，只立条）、tvboxconfig.json、szyshr best.json、lite.json、cygoy api.json、api2.json、list.txt（多仓指针，只立条）、url.txt（多仓指针，只立条）、nzsm tvbox.json、XC.json、ygbox.json、tvbox_merged.json。tvbox_new.json 的 jsDelivr 地址初版误立为独立配置条目，已并回 GitHub Pages 条目作镜像地址（现存配置数已扣减）。现存 786 个，spider 221 个。
- 成人内容清理：nzsm.json 多半成人（325/599），整份配置不立条、不提站；并入时跳过成人名站点 34 条、成人 host 站点 19 条、成人 api 8 条；合并后复核新增的 406 条全部干净。
- 跳过：探活 30 个配置地址，19 个存活、11 个仅可达（custom_sources.json 是裸列表、筛选 10 份是 CMS 筛选定义，均不是 TVBox 配置）；并入时跳过 2079 条已在库、394 条相对地址 api、67 条相对地址 ext。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十七批合并（2026-11-17 20:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（129 个仓库，对照累计已见 848 个仓库有 19 个新发现，其中 7 个是 19:06 轮已处理过的——19:06 的已见清单未含该轮自己的新仓库，本轮不再重复处理——真正新发现 12 个）；12 个已知仓库的 README 与根目录均无变化；mylazily latest/online/fastest 三份数据与 19:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 19:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表：16 个库外地址全部探活，0725.json 与道长 index.json 此前多轮探活均为死链，本轮不再重探；云星日记 1.m3u8 是直播列表，按 VOD-only 规则不收）。新发现中：zzq1234567890/tvbox1（配置合集：index.json 多仓指针 142 个地址、ok.json 77 站、jsm.json 272 站、feimao.json 62 站、moyu.json 99 站、aiwen.json 96 站、fantaiying.json 56 站、laowang.json 11 站全是成人名，未收）、SL-learn/SL-Sources（api_index.json 多仓指针 11 个地址、api_all.json 单文件 327 站、catmovie/config.json 小猫影视 19 站）、oyhh/tvbox-sources（tvbox-cms-direct.json 44 个直连实测 CMS 站、tvbox-stores-direct.json 多仓 42 个地址；README 说 raw 在国内直连超时，jsDelivr 最稳，已记为镜像地址）、neo-idea/STREAM-LIB-REPO（stream-lib-cat.json 多仓指针 8 个地址）、leonardoliu91/tvbox（tvbox.json 9 站）；其余新发现无源可收：Visupervi/TVBOX-AUTO 只是自动更新模板（其 sources.json 套用的是已在库的高天流云配置）、SH2413/tvbox-cleaner 是清理工具、977288629/tvbox-az 是 AVBox 播放器应用、storelah/sitepark/作品集/VOD 微服务源码均与 TVBox 配置无关：

- 新增点播源 113 条：CMS 接口 0 条；配置内站点 113 条（jsm.json 52 条：B站、独播资源、电影天堂、黑木耳、央视大全/新闻/综合/少儿等 drpy 站；api_all.json 42 条；fantaiying.json 16 条；小猫影视 config.json 3 条）。另有 433 条已有点播源补记了新出现的配置文件名；新增 spider 记录 4 条（fantaiying、moyu、aiwen、api_all 的 spider）。现存 17837 条。
- 新增 TVBox 配置 15 个：zzq index.json（多仓指针 142 个地址，只立条）、ok.json、jsm.json、fantaiying.json、feimao.json、moyu.json、aiwen.json，SL api_index.json（多仓指针，只立条）、api_all.json、catmovie config.json，oyhh tvbox-cms-direct.json（jsDelivr 记为镜像）、tvbox-stores-direct.json（多仓指针，jsDelivr 记为镜像），neo-idea stream-lib-cat.json（多仓指针，只立条）、leonardoliu91 tvbox.json、硬核指南多多多仓 duo.json（多仓指针，只立条）。现存 769 个，spider 217 个。
- 成人内容清理：laowang.json 11 站全是成人名，整份配置不立条、不提站（合并脚本新增规则——多半成人站点配置对直接 raw 地址也不立条）；并入时跳过成人名站点 19 条、成人 host 站点 10 条（索尼 suoniapi.com 等）、成人 api/URL 各 1 条；zzq 仓库里的 18sex/adult*.json、9918.json 成人配置未探未收。
- 跳过：探活 33 个配置地址，18 个存活（含 4 个经容错解析救回的 zzq 配置：index/jsm/fantaiying/laowang 的 JSON 有控制字符/尾逗号/注释，严格解析失败，合并脚本的容错加载器可正常读出）、8 个死链（多仓-134、星辰线路、吾爱、喵影视、小虎均为连接被关闭，半糖仙人 gitee 返回 423，meowcf 连接被关闭）、5 个 HTML 落地页（八仙多仓、多多跳回首页、djk1/gyckname 的 ghproxy 跳到 ghfast.top、adcc 的 agit.ai 返回 HTML）、1 个受限（ygbh.json GitLab 403 跳登录页）、1 个非配置（少儿频道 ymshaoer 实际是一张 PNG 图片）；并入时跳过 611 条已在库、176 条相对地址 ext、127 条相对地址 api、3 条坏地址/内网地址。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十六批合并（2026-11-17 19:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（129 个仓库，11 个是累计已见 848 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily latest/online/fastest 三份数据与 18:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 18:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表：除 0725.json 与道长 index.json 外均已在库，那两个此前多轮探活均为死链，本轮不再重探）。新发现中：yub168/myTvbox（config.json 100 站、mulConfig.json 多仓 3 个地址）、JeganZhao/TVBOX（tvbox_recommended.json 17 站）、deli6250/TVBOX（config.json 46 站）、superhe2004/tvbox-diy（bdjh.json 255 站、cang.json 多仓 23 个地址）、lylywayr/tv-matrix-core-tvbox-github-pages（output/tvbox.json 23 个健康度指针）、joneylee1978-lab/my-tvbox-config（tvbox_test.json 9 站）；其余新发现是成人站接口合集（bogege123/tvbox-interfaces 47 站全是成人站，未收未探）、非 TVBox 配置（jiji262/tvbox-sources 是专用 APK 的自定义 schema，只取了其中 CMS 地址比对）、直播源（yangfengln/tvbox-live，按 VOD-only 规则不收）与无关项目（开发者作品集、PHP 建站 CMS），均无源可收：

- 新增点播源 12 条：CMS 接口 0 条；配置内站点 12 条（全部来自 superhe bdjh.json：厂长、行动 APP、摆烂 4K、红红短剧、听界有声、儿童启蒙、少儿教育、小学/初中/高中课堂、俊老推送等 csp 爬虫站）。另有 260 条已有点播源补记了新出现的配置文件名；新增 spider 记录 0 条（bdjh.json 的 spider 是内网地址 172.18.0.1，已跳过不记）。现存 17724 条。
- 新增 TVBox 配置 8 个：yub168 config.json、yub168 mulConfig.json（多仓指针，只立条）、JeganZhao tvbox_recommended.json、deli6250 config.json、superhe bdjh.json、superhe cang.json（多仓指针，只立条）、lylywayr tvbox.json、joneylee tvbox_test.json。现存 754 个。
- 成人内容清理：CMS 探活 CK（ckzy.me）分类含伦理片，是成人站，未收；并入时跳过成人名站点 9 条（立播、辣椒资源等）、成人 host 站点 5 条（索尼 suoniapi.com、360zy.com）；jiji262 的 35 个 CMS 地址中除 CK 与索尼外全部已在库。合并后复核新增的 12 条全部干净。本轮还排除了 lylywayr tvbox.json 的 23 条“站点”：它们不是点播源，是指向他人配置文件的健康度指针（type 3 + api 为 .json 配置地址 + ext 为 health_score/latency_ms），已从点播源表删掉，只保留 tvbox.json 本身作为配置文件条目；合并脚本新增规则——type 3 站点的 api 是 .json/.txt 配置地址时按配置指针跳过，不再并入点播源。
- 跳过：探活 8 个配置地址全部存活；并入时跳过 373 条已在库、29 条相对地址 ext、1 条内网 spider。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十五批合并（2026-11-17 18:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（128 个仓库，8 个是累计已见 840 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily latest/online/fastest 三份数据与 17:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 17:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表：欧歌 api.json、挺好多仓 GYCK.json、安忆 api.json 均已在库）。新发现中：hjwp2026-cmd/self-tvbox（tvbox.json 多仓指针 2 个地址、无站点）、22yune/tvbox-kids（kids.json 儿童点播 9 个入口）、chanriver/mytvbox-source（cms-sources.json 52 站）；其余新发现是 TVBox 客户端源码（yagami-hue/MisaTV）、自建流媒体服务（outlook84/dashbox）、上游镜像仓库（mlzbest/upstream-sync）、字幕合板工具（luojiang419/DIT-source）与无关 CMS 建站软件（Jokudneh/formcms），均无源可收：

- 新增点播源 9 条：CMS 接口 0 条；配置内站点 9 条（全部来自 kids.json：儿童点播 9 个入口——搜索、按年龄、按学习路线、按内容类型、按专题、按名称、按来源、B站学习-按内容、B站学习-按作者，用 csp_Kids 爬虫）。另有 50 条已有点播源补记了新出现的配置文件名（cms-sources.json）；新增 spider 记录 2 条（kids.json 的 kids.jar、cms-sources.json 的 p.jar）。现存 17712 条。
- 新增 TVBox 配置 3 个：hjwp tvbox.json（多仓指针，只立条）、22yune kids.json、chanriver cms-sources.json。现存 746 个。
- 成人内容清理：并入时跳过成人名站点 1 条（玉兔 apiyutu）、成人 host 站点 1 条（索尼 suoniapi.com）；合并后复核新增的 9 条全部干净。本轮还修复了合并脚本的一个去重漏洞：chanriver 把 50 个 CMS 站标成 type 3，绕过了只对 type 0/1 生效的 CMS 去重，初版合并误加了 50 条与库内完全重复的 CMS 站，已回滚重合，只保留 9 条真正新增；今后绝对地址 api 已在库的 CMS 站不论 type 标注都按已在库处理，只补记配置文件名。
- 跳过：探活 3 个配置地址全部存活；CMS 橘猫 zitv.cc 403 受限（机房 IP 被挡），未收；并入时跳过 50 条已在库。chanriver sources.json 60 个 CMS 地址中 57 个已在库，config.json 的 20 个 api_site 除 360zy（成人站）外全部已在库。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十四批合并（2026-11-17 17:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（130 个仓库，10 个是累计已见 830 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily latest/online/fastest 三份数据与 16:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 16:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、360doc 配置教程：欧歌 api.json、挺好多仓 GYCK.json、安忆 api.json 均已在库）。新发现中：Basic-yao/TVBox（yao.json 99 站）、davisWeee/vod-hub（tvbox/config.json 13 个 CMS 站）、gitbochs/tvbox_url（config.json 自述 842 站、实测 1778 站，config_multi.json 多仓 100 个指针）、flybywind-1986/tvbox-config（config.json 多仓 9 个地址）；其余新发现是成人专用 spider（larui762/tvbox18 四站聚合 asmr/jable/supjav/missav，未收未探）、直播源（Kinghuchao/tvbox-live CCTV 直播，按 VOD-only 规则不收）、TV 客户端源码（zysaii/m3u_tvbox）、源站监控工具（rzhnrhjr6j-cloud/tvbox-source-monitor）与无关项目（beacon8832/XGLUMeMD 豆瓣毕设）：

- 新增点播源 426 条：CMS 接口 0 条；配置内站点 426 条（主要来自 gitbochs config.json：T4 聚合/CloudStream、新 4K 采集站、动漫/短剧/影视 APP 站等；yao.json 1 条：豆瓣点播）。另有 619 条已有点播源补记了新出现的配置文件名；新增 spider 记录 1 条（yao.json 用 ghproxy 镜像的 jpg 爬虫包）。现存 17703 条。
- 新增 TVBox 配置 5 个：Basic-yao yao.json、davisWeee tvbox/config.json、gitbochs config.json、gitbochs config_multi.json（多仓指针，只立条）、flybywind config.json（多仓 9 个地址）。现存 743 个。
- 成人内容清理：并入时跳过成人名站点 76 条、成人 api 7 条、成人 host 站点 9 条（360zy.com、索尼 suoniapi.com）、成人 URL 1 条；合并后复核又发现 4 条漏网（fulleroticmovies 怀旧经典、MasexTV、2048 基地、91 短剧，文件名含成人内容）已从点播源中删除，净增 426 条。
- 跳过：探活 6 个配置地址：存活 5 个、仅可达 1 条（jeffwxg tvbox.json JSON 格式损坏，含未加引号的 spider 行，未收）；并入时跳过 743 条已在库、487 条相对 api、134 条相对 ext、3 条无效/私有 api。gitbochs config.json 的 1778 站中绝大多数已在库或被过滤；davisWeee 13 站中仅虎牙采集站 /at/json 一种新接口形式新增，其余均已在库，360zy.com 为成人站未收。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十三批合并（2026-11-17 16:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（132 个仓库，9 个是累计已见 821 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily latest 74 条无新增（字节差异只是时间戳），online 61→63 条（百花已在库；如意 api.ryzy.com 探活跳转到 ww16.ryzy.com 落地页，不是 CMS 接口，未收），fastest 20 条轮换、10 条“新增”接口均已在库；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 15:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、360doc 配置教程、MacCMS 采集接口文档：厂长、快车 2 个资源站均已在库）。新发现中：Lettte/tvbox-custom（jsm-plus.json 165 站）、LIUYANGZHEN/TVbox（文件“2026.11.17”，164 站，与 jsm-plus 同源，0 条新增）、xlg99/tvbox-api-backup（duocang.json 多仓 + X4少儿频道/X4更新专用接口/X4菠菜pro/X4菠菜园/嗷呜/摸鱼 6 份配置）；其余新发现是成人专用配置（ansun1714 my-private-api.json“亚洲性学点播接口”62 站全成人、Lettte custom-sites.json 全是 MissAV/JavDb，均未收未探）、空仓库（Kai520818/TVbox1 只有 README）、iOS 客户端源码（lee07160/PocketBox，无源可收）、CMS 建站软件（moponer/catter-cms）与无关插件（clawnify/OpenFramerSync）：

- 新增点播源 170 条：CMS 接口 0 条；配置内站点 170 条（主要来自 X4菠菜pro.json 53 条：都司/非凡/卧龙/最大等 CMS 站、短剧/动漫/音乐/少儿教育等 APP 站；摸鱼.json 47 条：玩偶/木偶/摆烂/晚晴等 4K 站、星河共影等；嗷呜.json 33 条：玩偶/木偶 4K、韩剧/瓜子/金牌秒播等；X4少儿频道.json 25 条：哔哩合集、兔小贝、童趣、小灯塔系列、幼小衔接等；jsm-plus.json 8 条：云播/未来 APP 站、少儿教育与小学/初中/高中课堂；X4更新专用接口.json 3 条：菠菜园下载、奇奇副本/本地等应用市场包；X4菠菜园.json 1 条）。“菠菜”只是 X4 配置的品牌名，站点本身是常规点播源。另有 507 条已有点播源补记了新出现的配置文件名；新增 spider 记录 8 条。现存 17277 条。
- 新增 TVBox 配置 9 个：Lettte jsm-plus.json、LIUYANGZHEN 2026.11.17、xlg99 duocang.json（多仓指针，只立条）、X4少儿频道.json、X4更新专用接口.json、X4菠菜pro.json、X4菠菜园.json、嗷呜.json、摸鱼.json。现存 738 个。
- 成人内容清理：并入时跳过成人名站点 7 条（MissAV、JavDb、经典┃推荐、Sed┃4K、LBV┃2K、立播 4K、Seed 4K）、成人 api 2 条（种子 4K SeedHub）、成人 host 站点 8 条（索尼 suoniapi.com 6 条、360zy.com 2 条）。
- 跳过：探活 11 个配置地址：存活 9 个、死链 2 条（ZTHA000 djk1.json 404，52bsj xiaohu 远端断开）；CMS 如意 api.ryzy.com 跳转落地页，未收；并入时跳过 510 条已在库、35 条相对 api、1 条相对 ext。xlg99 cjlist.txt 53 条 CMS 接口除 360zy、索尼两个成人站外全部已在库；xlg99 潇洒/王二小/饭太硬/海量采集/海量py 是已在库配置的同名副本，未重复立条；134.122.170.64 dc.json、yydsys.top/duo、gitee lichuanrui chuanshuo.json、freed.yuanhsing.cf meowcf.json、52bsj wuai 昨天 16:06–17:06 已探明死链/落地页，本轮未重试。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十二批合并（2026-11-17 15:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（136 个仓库，6 个是累计已见 815 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 14:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 14:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、6mf 影视仓配置页、MacCMS 采集接口文档：量子、非凡、暴风、卧龙、快车 5 个资源站均已在库）。新发现中：gaoshangshuai/tvbox-test（XPTV 配置仓库，tvbox/vod/vod2/cms/cms_jjw/allinone/xptvtest/pan.json 共 8 份配置）、281049519/tvbox-live-config（config.json 49 站）、huangxinyueus/tvbox-laqu（sources_list.txt 给出潇洒/王小二/聚玩等地址）；其余新发现是 iptv-api 直播工具的 fork（tyxthl/iptv-api，按 VOD-only 规则不收）、TVBox 客户端源码（cxapython/tvbox-arm，无源可收）与无关写作 Skill（cnYui/mediastorm-koubo）：

- 新增点播源 57 条：CMS 接口 0 条；配置内站点 57 条（主要来自潇洒.json 116 站配置 24 条：布布/马猴/剧圈/半日/天堂/橘汁/华谊/苹果等 APP 站、哔哩合集/音乐/听书/相声/小品/戏曲、少儿教育与小学/初中/高中课堂；潇洒 api.json 8 条：怀桑、鸭社 4K、七猫/河马/星芽短剧等；聚玩.json 7 条；281049519 config.json 7 条：玩偶哥哥┃4K弹幕、盘她┃夸父、盘他┃嘟嘟等云盘/搜搜站；gaoshangshuai allinone.json 3 条：豆瓣┃点播、腐剧┃点播、宝片┃点播，cms.json 1 条：魔都资源网，cms_jjw.json 1 条：剧集屋，vod/vod2 5 条：金牌影院、一席、233动漫、优酷视频、4K影视，pan.json 1 条：玩偶哥哥 PAN）。另有 192 条已有点播源补记了新出现的配置文件名；新增 spider 记录 2 条（聚玩.json 用 Yoursmile.jar、潇洒.json 用 png 爬虫包）。现存 17107 条。
- 新增 TVBox 配置 12 个：gaoshangshuai tvbox.json、vod.json、vod2.json、cms.json、cms_jjw.json、allinone.json、xptvtest.json、pan.json，281049519 config.json，潇洒 api.json（cnb.cool）、聚玩.json、潇洒.json。现存 729 个。
- 成人内容清理：并入时跳过成人名站点 3 条（小黄人、豆豆片单、LibVio）、成人 api 3 条（立播、种子 4K）、成人 host 站点 3 条（360zy、索尼 suoniapi.com）。
- 跳过：探活 19 个配置地址：存活 12 个、死链 3 条（jijietvbox.lol xiaosha.json、jieluntan-fty.json 均 404，cdn.qiaoji8.com tvbox.json 远端断开）、HTML 落地页 2 条（安忆 52011.top、王二小 tv.xn--yhqu5zs87a.top）、仅可达 2 条（肥猫 fm.gif 实为图片非 JSON、王小二 ai.xn--4kq62z5rby2qupq9ub.top 非 JSON）；并入时跳过 312 条已在库、8 条相对 ext、8 条相对 api。潇洒 api.json 的 127 站与潇洒.json 的 116 站中绝大多数已在库或被过滤。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十一批合并（2026-11-17 14:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（134 个仓库，7 个是累计已见 705 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 13:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 13:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、6mf 影视仓配置页、360doc 配置教程、MacCMS 采集接口文档：暴风、芒果、非凡、量子、快车 5 个资源站均已在库；星夜 xyezy 与越南 vnzyz 于 10:06 已探明为成人分类站，不收）。新发现中：jhzone/TVbox（tvbox.json 10 站）、no7ren/tvbox（tvbox_full.json 1433 站、0607.json 56 站）；其余新发现是 iptv-api 直播工具的 fork（woall/TV、rustin1229/TV、hyboyxo/darkelf123 的 iptv-api，按 VOD-only 规则不收）与 Flutter 影视 App 客户端骨架（ojkky/cineview-app，无源可收）：

- 新增点播源 26 条：CMS 接口 0 条；配置内站点 26 条（主要来自 no7ren 0607.json 21 条：卧龙资源、厂长┃无广、农民┃秒播、酷奇┃MV、明星┃MV/演唱会、儿童┃启蒙、少儿┃教育、小学/初中/高中┃课堂等；tvbox_full.json 5 条：天涯资源、麦田┃网页、66┃大片、追影┃猫猫、三五┃电影）。另有 73 条已有点播源补记了新出现的配置文件名；新增 spider 记录 1 条（no7ren 0607.json 用 fan.txt 爬虫包）。现存 17050 条。
- 新增 TVBox 配置 3 个：jhzone tvbox.json、no7ren tvbox_full.json、0607.json。现存 717 个。
- 成人内容清理：并入时跳过成人名站点 113 条、成人 api 3 条、成人 URL 3 条、成人 host 站点 13 条（索尼 suoniapi.com 等）；longer519 config-lite.json 因 20 站中 14 站为成人名，整配置未收；longer519 gh-proxy 版 config.json 是已在库配置的镜像，不再单独立条。
- 跳过：探活 18 个配置地址：存活 5 个、死链 7 条（PizazzGY 影视/磁力/云盘_api 三份均 404 已下架、wya6 yc.json 456、8.210.232.168 远端断开、52bsj 多仓签名地址远端断开、小米 DEMO.json 404）、HTML 落地页 3 条（bp.tvbox.cam、ghproxy 两次跳到 ghfast.top 落地页）、受限 1 条（tv.nxog.top/m/ 403）、仅可达 2 条（no7ren 05134k.json 含非法字符解析失败、jihulab ymshaoer 非 JSON）；并入时跳过 1180 条已在库、153 条相对 ext、77 条相对 api。no7ren tvbox_full.json 的 1433 站中绝大多数已在库或被过滤，仅新增 5 条。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第四十批合并（2026-11-17 13:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（131 个仓库，32 个是累计已见 769 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 11:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件与 11:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、MacCMS 文档的采集接口一览：暴风、芒果两个资源站均已在库）。新发现中：tqx5201/tvbox（config.json 23 站、fty/config.json 49 站）、yhc7scorpio/tv-sources（源自动择优，每天 GitHub Actions 实测扫描上游，tvbox.json 与 tvbox_fallback.json 各 135 站，内容相同）、JOVL9527/tvbox-source（自动构建输出，sites.json 与 source.json 各 150 站，内容相同，2026-11-17 当天更新）、zzxw/tvboxkeeper（源站守望者，多仓.json 54 个仓、 多仓-lite.json 8 个仓）；shawun2026/fwd-rex-webhtv 是 Forward/Rex 模块转 WebHTV 的适配器，vod_lite.json 15 站全是相对 api 且多为成人模块（91成人短剧、禁果短剧、红果黄剧、蜜桃视频等），整配置未收；其余新发现多为 iptv-api 直播源工具的 fork（按 VOD-only 规则不收）、TVBox 客户端源码（Gladglod/MBox、andyhang1980/TVBoxOS、cubacupa/myTVBox）与无关 CMS/工具，无可并入项：

- 新增点播源 56 条：CMS 接口 0 条；配置内站点 56 条（主要来自 JOVL9527 sites.json 51 条：搜索·豆瓣、飞宇影院、华数·影视、热播/布布/马猴/剧圈/半日/天堂/橘汁等 APP 站；tqx5201 config.json 5 条：AList、洋葱学园、界影视.py、电影猎手.py、儿童┃启蒙）。另有 361 条已有点播源补记了新出现的配置文件名；新增 spider 记录 2 条（JOVL9527 sites.json 用 qist spider.jar、yhc7scorpio tvbox_fallback.json 用 ghfast 镜像的 pg_upgraded.jar）。现存 17024 条。
- 新增 TVBox 配置 8 个：tqx5201 config.json、fty/config.json、yhc7scorpio tvbox.json、tvbox_fallback.json、JOVL9527 sites.json、source.json、zzxw 多仓.json、多仓-lite.json（多仓文件只立条，不单独收其 storeHouse 指向的 54/8 个子配置）。现存 714 个。
- 成人内容清理：并入时跳过成人名站点 9 条（豆豆片单、SeedHub、LIBVIO/立播、白嫖影视等）、成人 api 3 条（csp_LibvioGuard 立播、csp_SeedHub 种子）、成人 URL 6 条（索尼 suoniapi.com 采集接口）。
- 跳过：探活 13 个配置地址：存活 8 个、死链 3 条（半糖仙人 gitee 423、9xi4o.tk 远端断开、yc.wya6.cn wykj.php 456）、HTML 落地页 2 条（摸鱼儿、宝盒）；并入时跳过 404 条已在库、122 条相对 ext、42 条相对 api、9 条成人名站点、3 条成人 api、6 条成人 URL。yhc7scorpio 两份配置的 135 站与 JOVL9527 source.json 的 150 站全部已在库或被过滤，0 条新增。硬核指南页面上已在库的 3 个地址（天神IY、700sjro44343 tv.json、home.jundie.top top98.json）不再重复立条。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

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

## 第二十批合并（2026-11-16 08:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用点播关键词（tvbox、drpy、影视源、猫影视、cms-api、影视仓、vod-source、影视接口）搜 GitHub，122 个仓库；其中资源类：TVboxorg/TVbox（接口汇总与可用性探测）、mylazily/ziyuanzhan（CMS 采集站监控，74 条）、adminouyang/231006（tvbox 配置搜集，209★）、jiusanzhou/tvbox、zhuzhuyule/juhe-subhub（订阅自动检测拼装）、ouyushan/tvbox-cfg、Inliang/tvbox、guxia66898/tvbox-hub 等；网页搜索另发现 mac-cms.com 的 CMS 资源站一览与 viptv/硬核指南的配置地址：

- 新增点播源 1849 条：CMS 接口 5 条（厂长、茅台、天涯、豪华、虎牙，均逐个探活 `?ac=list` 返回真 CMS JSON，且分类表检查通过）、配置内站点 1844 条（主要来自 tvbox_full.json、zijian-full.json、tvbox.json、official.json、tv.json 等聚合配置）。现存 2666 条。另有 1484 条已有点播源补记了新出现的配置文件名；新增 spider 记录 9 条。
- 新增 TVBox 配置 52 个：TVboxorg 的 tvbox.json 与 official.json、juhe-subhub 的 merged.json/tvbox.json/merged-manual.json、ouyushan 的 multi.json、Inliang 的 zijian.json/zijian-full.json、Lightconer、fengzhiku123、tvbox-hub 的 merged.json/curated.json、HowKongFish 的 merged.json、tangyou254-design 的 vod.json/duocang.json、Lingeng27 的 aggregate.json/tv.json、25175/tvyuan 的 tvbox.json/tvbox_full.json/tvbox_multi.json、adminouyang 的影视仓库.json 与 13 个单仓 txt、zqs1qiwan 的 laobai.json、qist 的 xiaosa/api.json、xhztv 的 xhz、摸鱼儿 fish.json、liucn 的 m.json（jsdelivr 镜像）、9280.kstore 的 newwex.json/wex.json 等。现存 146 个。
- 成人内容清理：本轮抽取时发现历史遗留问题——vod-sources.json 里已有 50 条成人条目（18AV、Hanime、JavBus/JavDb、LIBVIO/立播、MissAV、Netflav、SeedHub、XOJav、91麻豆、精品、黄AV、155、森林、滴滴、玉兔、白嫖、色猫、辣椒、乐播、老色逼、jkun，以及直接以“成人05–成人27”命名的 CMS 站），多为早先从 9918.json/99188.json 等配置抽取时混入。按“成人内容永不进公开仓库”的规则，本轮已全部删除（清单见本地 hourly/adult-purge-2026-11-16-0806.json），现存 2666 条已不含上述条目。教训：只看站点名会漏检——“爱坤联盟”实为 jkun 站、“立播”实为 Libvio，本轮起并入时同时检查 api 地址（域名/规则名）是否命中成人词表；相对地址（./lib/…）的 ext 无法独立使用，本轮起不再收录。
- 跳过：重复 1587 条；成人 180 条（配置内成人名站点 167 条、api 地址命中成人词 9 条、成人 URL 精确命中 4 条）；相对地址 911 条（api 相对路径 263 条、ext 相对路径 648 条）；不可达 15 条（快车、豆瓣 CMS 远端无响应；pandown、wya6 的 456、lyyytv 的 404、tvbox.vip 的 404、raw.iqiq.io 两处、52bsj 两处、meowcf 等）；受限 1 条（jihulab ok.txt 401）；HTML 落地页 9 条（agit.ai 两处、weixine、yydsys、fty.888484、iyouhun、菜妮丝、天空资源域名停放）；非配置内容 6 条（TVboxorg list.json 是健康检查报告、tvbox-hub 的 tvbox.json 内容为 null、月光宝盒与 yoursmile66 的 XC.json 是十六进制加密配置、jzy.txt 实为 JPEG 图片、tv.999888987.xyz 非 JSON）。6 个配置（Moew.txt、小米.txt、挺好.txt、欧歌.txt、肥猫.txt、骚零.txt）因手写 JSON 宽松语法（行内字符串换行等）无法解析，站点未抽取，地址已收录。另：多仓指针配置（TVboxorg tvbox.json、juhe-subhub merged、tvbox-hub merged/curated 等）指向数百个更深层的配置地址，留待后续轮次逐批探活。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十八批合并（2026-11-16 16:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox订阅、影视源、drpy、猫影视、影视接口、点播源）搜 GitHub（122 个仓库，55 个是上一轮没见过的），新发现：kygn2000-bot/tvbox-source（LibreTV/TVBox 多格式源清单，每天自动采集实测）、Alianbye/tvbox（多仓订阅配置）、dubin3520036/n1-tvbox（N1 聚合订阅）、wangguo0/tvbox-sub（点播+直播自动聚合订阅，每 3 天 CI 合并）、daletyler1737/tvs-source（TVS 订阅：8 个实测 CMS + 227 个 drpy 站）、smallniangao/TVBoxHome（影视仓接口地址大全）、Night0317/dm-tvbox（动漫专属订阅源）、evenbsies/tvbox-harvest（从 Issue 采集点播源生成订阅）、SikROo/huangguo-spider（黄果短剧 FongMi 源）、erxuw196/e915779-rgb/haojun19980728-prog 的 LibreTV 源清单（每天自动采集实测，点播源带 isAdult 标记）；网页搜索补新地址（硬核指南影视仓/TVBox 列表、360doc 教程页：月光宝盒 jihulab dc.json、52bsj 星河多仓、pandown、yydsys 等）；mylazily/ziyuanzhan 重新拉取最新数据（与 15:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本；本轮新发现的多仓指针配置（15487.kstore.space 0619多线.txt、王二小放牛娃 txt、pspoia 多仓源.txt）里的地址当轮下探第二波，又挖出 59 个地址、36 个存活：

- 新增点播源 1133 条：CMS 接口 0 条（360 资源站 seaxml 变体一度误收、已删除；越南资源站 vnzyz 分类表全是丝袜美腿/盗撮未收；索尼采集站 suonizy 探活为成人内容未收）；配置内站点 1133 条（主要来自 wangguo0 merged.json 1705 站、dubin3520036 aggregated.json 596 站、daletyler1737 tvs.json 233 站、kygn2000-bot libretv-vod-full.json 86 站、mosoras tvbox.json 160 站、Alianbye config.json 104 站、gaotianliuyun js.json 298 站、hucongrong fxz.json 335 站、jiekou.netlify.app svip.json 245 站、xmbjm svip.json 245 站等，去重后）。另有 2706 条已有点播源补记了新出现的配置文件名；新增 spider 记录 24 条。现存 10744 条。
- 新增 TVBox 配置 66 个（净增）：kygn2000-bot 七文件（dxawi/libretv-vod-full/libretv-vod-direct/movie-config/wex-config/vod-selected/movie-cn）、Alianbye config.json、dubin3520036 aggregated.json、hany1123 sub.json、becauseyour config.json、pspoia 饭太硬.json/多仓源.txt、mosoras tvbox.json、Jasonjie1991 cms.json（reachable，未抽取站点）、Night0317 dm_entry/dm_all/dm_src1–6、SikROo all_sources_config.json（jsdelivr 记 raw 直链）、daletyler1737 tvs.json、sylvan97 multi.json、wangguo0 merged.json、anbola tvbox_clean.json、9280.kstore.space aiwex.json、gaotianliuyun js.json（refs 直链）、tv.sxi.qzz.io jsm.json、yydsok api.json、jihulab 机缘巧盒凯弟两处、CatVodSpider demo.json、150.158.52.248 bbm.json、gitee 初心.json、cnmb xnf.json、hucongrong fxz.json、11405.kstore.space qk4k.json、jiekou.netlify.app svip.json、ghfast hanhan8127 hanXC.json、jihulab yueer.json、tvjuhe.mitetech.cn、cnb 20000.json、xhztv 神仙 api.json、cttv ctys.json、gitee x4c.json、jikefuye tvbox.json、15487.kstore.space 七星在线/宜优精选/老农民/天微/酷喵系列 txt、meow.668yun.top 酷喵1.0.txt、王二小放牛娃 txt 两个镜像、xmbjm svip.json（raw 直链 + gh-proxy 镜像）。现存 487 个。另：0827.json 的 gh-proxy 地址记为已有 raw 条目的 mirror_url，不再单独立条。
- 成人内容清理：360zy 的 seaxml 变体地址（api.php/seaxml/vod）一度被误收为 CMS——合并脚本的新 CMS 检查只看了站点名和精确 URL 黑名单，没查 api 域名是否命中成人 host 表；已删除该条目，seaxml 地址已补进成人 URL 黑名单，脚本已修（新 CMS 先查成人 host）。544609136 vod_slim.json（37/54 成人名）与 e915779 tvbox.json（31/57 成人名）本轮又被合并脚本重新立为配置条目——脚本只在站点抽取层拦截多为成人配置，配置立条分支没有同样的检查；两条已手工去掉，脚本已修（立条前同样检查）。SikROo huangguo_web_spider_config.json 12 站全是成人名、整配置未收。360zy/vnzyz/suonizy 三站均未收。
- 跳过：第一波探活 70 个地址：存活 35 个配置 + 3 个 CMS（CMS 均为成人站未收、另 1 个成人内容）、死链 17 条（box.ufuzi、fty.xxooo.cf、cdn.qiaoji8、meowtv、miqk/mpanso DEMO、9877.kstore.space 三处 404、gitee 423 两处、9xi4o.tk、yc.wya6.cn 456、52bsj 星河多仓、134.122.170.64、pandown.pro）、受限 3 条（tv.nxog.top 403、6296.kstore.space 401、9877.kstore.space single.json 403）、HTML 落地页 3 条（5.180189.com 跳 v1 首页、0.12yue.de5.net、yydsys.top）、reachable 8 条（tarynwyj config.json、your smile66 XC.json、Alianbye sun.json、Jasonjie1991 cms.json、tv.lxyy.club、bd.qiqiv.cn 666.json、gitcode 版本.json、gh-proxy.org 极客小盒）；第二波探活 59 个地址：存活 36 个、死链 16 条、受限 2 条、HTML 落地页 1 条、reachable 4 条；并入时跳过 5366 条（已在库 3412 条、相对 ext 938 条、相对 api 794 条、成人名站点 152 条、成人 host 37 条、成人 api 14 条、无 api 9 条、整配置多为成人 4 个、配置无法解析 3 个、CMS 成人 URL 1 条、成人 URL 2 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十九批合并（2026-11-17 11:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（129 个仓库，12 个是累计已见 757 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 10:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404；zknjjjx 13 个上游 conf 文件中 11 个与 10:06 字节一致，2 个有变化（王二小、饭太硬，站点改名 Wex*Guard→AiNew*Guard）；网页搜索补新地址（硬核指南 TVBox/影视仓列表、MacCMS 文档的采集接口一览）。新发现的 TVBox 相关仓库中：raychan239/tvbox（肥猫/饭太硬/潇洒三家聚合订阅，subs 下 all/pan/play/sources 四种共 12 份配置）、FLAG12321/tvboxresource（merged.json 100 站、multi.json 多仓指针、single_list.json 放牛娃 newwex 双地址）、lichenzhou225/tvboxtest（output/merged.json 100 站）；其余新发现多为 TvBox 插件源码（muedsa 的 novipnoad/bilibili/ha 三个插件）、AI 漫剧创作平台（shijue-aid/aid-studio）、TVBox 桌面端（angyuang/tvbox-desktop，samples 是示例占位地址与 5 个已在库的苹果CMS站）、Flutter 追剧客户端（zhao22307-afk/yiqikan）与无关 CMS/旁白工具，无可并入项；jincg99/tvbox 只有 live.txt，按 VOD-only 规则不收：

- 新增点播源 0 条：18 份存活配置共 1076 个站点全部已在库或被过滤——1007 条已在库（raychan 三家、FLAG/lichenzhou 的 merged.json、放牛娃 newwex 与王二小/饭太硬上游四份是同一批 2026-11-17 当天更新的 AiNew 系快照，互相高度重合；改名后的 AiNew*Guard 站点 10:06 轮已随 my57575757 aggregate.json 收过）。另有 579 条已有点播源补记了新出现的配置文件名；新增 spider 记录 12 条（肥猫四份共用 gelonghui 爬虫包、饭太硬四份共用 meitudata 爬虫包、潇洒四份共用 moji.com 爬虫包）。现存 16968 条。
- 新增 TVBox 配置 14 个：raychan239 subs 12 份（fm-all/fm-pan/fm-play/fm-sources、fty-all/fty-pan/fty-play/fty-sources、wex-all/wex-pan/wex-play/wex-sources）、FLAG12321 merged.json、lichenzhou225 merged.json。放牛娃 newwex 双地址与王二小/饭太硬上游两份已在库内，不再重复立条。现存 706 个。
- 成人内容清理：并入时跳过成人名站点 18 条（立播/黄人/豆豆片单等）、成人 api 4 条（csp_LibvioGuard 立播）。
- 跳过：探活 18 个配置地址全部存活，死链/受限/HTML 落地页 0 条；并入时跳过 1007 条已在库、43 条相对 ext、4 条相对 api、18 条成人名站点、4 条成人 api。angyuang-public 的 5 个苹果CMS站（非凡/量子/电影天堂/光速/素博）均已在库，本轮未探 CMS。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十八批合并（2026-11-17 10:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（131 个仓库，11 个是累计已见 753 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 08:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本；zknjjjx 13 个上游 conf 文件与 08:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、MacCMS 文档的采集接口一览、影视站长圈/星夜资源站）。新发现的 TVBox 相关仓库中：Captain-2019/tvbox-sync（TVBox 源自动同步，聚合 tvbox.json 含 618 站）、my57575757/tvbox-agg-sub（聚合订阅 aggregate.json 含 2686 站）、InkiChang/tvbox-cms-source（每日自动重建的 CMS 订阅源，61 站，2026-11-17 当天更新）、mlzbest/tvbox-api-backup（误道者整理的海量接口备份，含海量采集聚合、海量py聚合、FongMI、clun 等）、pengcgg/tvbox-api-backup（与 mlzbest 同构，取其一即可）、lqdloveworld/zhuiju-nav（追剧导航，87 条资源，38 条未进 guides 库——小说/电子书类居多，guides 暂无小说分类，本轮未并入）、child9527/tvbox（json/ 只有二维码图片，无可用配置）；ballad0324/HoopoeTV（TVBox 定制壳客户端）、nzsm/tv-build（TVBox 云编译）、maglcal/angel-screening（飞牛影视桌面客户端）是客户端不是源；4yt1k/m3u-autoupdate 是直播源自动更新，按 VOD-only 规则不收：

- 新增点播源 574 条：CMS 接口 0 条；配置内站点 574 条（主要来自 my57575757 aggregate.json 397 条、mlzbest 海量py聚合接口.json 84 条、Captain-2019 tvbox.json 59 条、海量采集聚合接口.json 14 条、更新专用接口.json 10 条、InkiChang source.json 5 条、FongMI线路.json 4 条、clun.json 1 条，去重后）。另有 1033 条已有点播源补记了新出现的配置文件名；新增 spider 记录 5 条（海量采集聚合/海量py 共用 mpimg.cn 爬虫包、FongMI 用 gaotianliuyun custom_spider.jar、clun 用 clun.top xs.jar、更新专用接口用另一 mpimg.cn 包）。现存 16968 条。
- 新增 TVBox 配置 11 个：Captain-2019 tvbox.json、my57575757 aggregate.json、InkiChang source.json、mlzbest 海量采集聚合接口.json/FongMI线路.json/clun.json/海量py聚合接口.json/更新专用接口.json、老张 api.json（zhangqun1818.serv00.net）、周J box（gh-proxy）、小米 demo.json（CatVodSpider demo）。现存 692 个。
- 成人内容清理：4 个新 CMS 站 `?ac=list` 全部含成人分类未收——360 资源站（伦理片）、越南资源站（亚洲情色/热门女优/无码专区/伦理三级/丝袜美腿/JAV高清）、f-1.cc 看看资源（自拍偷拍）、星夜资源站（女优明星/AV解说/偷拍偷窥/三级伦理/日韩无码/动漫激情）；InkiChang 61 站里 23 个新 host 中 21 个是成人名站（奶香香、辣椒、JKUN、黑料、索尼、大X子、精品X、细胞、155、森林、奥斯卡、麻豆、乐播、黄色仓库、玉兔、小鸡、滴滴、搜av、豆豆、杏吧、新极品）未收；并入时另跳过成人名站点 51 条、成人 URL 31 条、成人 api 2 条。
- 跳过：探活 35 个配置地址：存活 11 个、死链 13 条（半糖仙人 gitee 423、驸马/影探/小苹果 404、9xi4o/巧计/真六/讴歌/集多/凯弟2线远端断开、无意云 wykj.php 456、道长 gitlab 404、潇洒 one.json 404）、受限 5 条（xhww.fun 403 跳域名停放、潇洒 sun.json 403、短剧 cnb 403、肥猫 403、lqdloveworld 潇洒 cnb 403）、HTML 落地页 2 条（菜妮丝 tv.xn--yhqu5zs87a.top、传说 tjf1100 跳 888 域名）、reachable 4 条（ymz1231 与东篱 chigua.eu.org 200 非 JSON、裤佬 Jsnzkpg 多对象 JSON、裤佬T4 t4.json 是 drpy 规则文件无 sites 键）；并入时跳过 1502 条已在库、1029 条相对 api、739 条相对 ext、51 条成人名站点、31 条成人 URL、2 条成人 api、8 条无 api、2 条坏/私有 api。mlzbest api_list 里 47 个非库内地址多为 HTML 落地页与已知失效线路，仅老张/周J/小米 3 个存活已收。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十七批合并（2026-11-17 09:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用 8 个关键词搜 GitHub（129 个仓库，38 个是累计已见 716 个仓库之外的新发现）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 08:06 字节完全一致；applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本；zknjjjx 13 个上游 conf 文件与 08:06 字节完全一致；网页搜索补新地址（硬核指南 TVBox/影视仓列表、MacCMS 文档的采集接口一览）。新发现的 TVBox 相关仓库中：bhsherry/vod-source-feed（Zyfun 点播源清单）、NavyL/tv-sub（自建影视订阅镜像，每 6 小时自动更新）、ZQingGang/tvbox（自动聚合 tvbox.json）、JianghaoPi/my-tvbox-sources（聚合 aggregate.json）、baggiobatistuta/my-tvbox（单仓 dancang.json）、testtestqq/tvbox-config、WKC0001/tvbox-independent（独立聚合 dc.json/api.json）、ewctt/tvbox、ZHOUYU86/tvbox-sources（多仓 all.json）、panpeach/tvbox、willgood2024/tvbox-auto、ouhaibo1980/tvbox、aa3151036158/tvbox-config、lngscym/tvbox；其余新发现多为网页 CMS 框架（Natheo、CoCreateJS 等，非视频 CMS）、播放器客户端（DramaCube、patina-iptv）与分销后台，无可并入项；hx1ang/tvbox-sport 只有体育直播爬虫站，按 VOD-only 规则不收：

- 新增点播源 62 条：CMS 接口 0 条；配置内站点 62 条（主要来自 ewctt box.json 22 条、lngscym 单仓精选.json 15 条、NavyL best.json 14 条、WKC api.json 8 条、willgood tvbox_clean.json 3 条，去重后；含艾旦影视、极速资源2、大师兄影视、闪电资源等 CMS 接口与玩偶哥哥、观影网盘、皮卡搜等爬虫站）。另有 430 条已有点播源补记了新出现的配置文件名；新增 spider 记录 3 条（baggiobatistuta dancang.json、NavyL best.json、lngscym 单仓精选.json）。现存 16394 条。
- 新增 TVBox 配置 17 个：bhsherry zyfun-vod-import.json、ouhaibo1980 dc2.txt（多仓指针，22 条缓存线路）、ZQingGang tvbox.json（storeHouse 26 个）、baggiobatistuta dancang.json、testtestqq tvbox.json、WKC api.json、ewctt box.json、ZHOUYU86 all.json（多仓指针，16 个子接口）、panpeach 单仓.json（多仓指针，7 个）、willgood tvbox_clean.json、NavyL best.json/multi.json/tv.json、aa3151036158 多仓订阅.json、lngscym 单仓精选.json/多仓订阅.json、ZTHA000 gyckname.json（storeHouse 2 个）。JianghaoPi aggregate.json 已在库，不重复立条。现存 681 个。
- 成人内容清理：360 资源站 class 表含伦理片未收；天空资源站跳转到停放页、不是 CMS JSON 未收；索尼 suoniapi.com 带 `?ac=list` 的变体一度误收（normalize_url 保留 query，未命中无 query 的黑名单条目），已删除，并入脚本已补 host 级拦截，今后同 host 任何路径/参数都直接拦截；并入时另跳过成人名站点 16 条、成人 URL 11 条、成人 api 1 条（立播 Libvio、索尼、越南 vnzyz、CK 资源等均未收）。
- 跳过：探活 34 个地址：存活 18 个配置、死链 8 条（ZTHA djk1.json 404、传说 chuanshuo.json 423、吾爱/小虎/ip-dc/meowcf/巧记远端断开、wya6 yc.json 456）、受限 3 条（jihulab 小胡 401、gitlab ygbh.json 403 跳登录、tv.nxog.top 403）、HTML 落地页 4 条（八仙多仓、多多 duo 跳首页、agit.ai adcc、bp.tvbox.cam）、reachable 1 条（willgood tvbox.json 是 JSON 数组指针，改收其 tvbox_clean.json）；并入时跳过 726 条已在库、98 条相对 ext、23 条相对 api、16 条成人名站点、11 条成人 URL、1 条成人 api、8 条无 api、1 条坏/私有 api。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十六批合并（2026-11-17 00:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox配置、影视仓接口、影视源、drpy规则、猫影视接口、cms采集接口）搜 GitHub（50 个仓库，7 个是上一轮没见过的）；12 个已知仓库的 README 与根目录均无变化；mylazily/ziyuanzhan 三份数据与 23:06 完全一致；applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本（已挖过，不重挖）；zknjjjx 13 个上游 conf 文件与 23:06 完全一致；硬核指南两页所列配置地址与此前一致，无新增（此前已探过不通过的 12 个本轮不再重复探活）。新发现的 7 个仓库中：wan7up/tvbox-source（单仓聚合配置）、lebond2021/mediasources（4664 站聚合配置）、yangclaw2026-png/tvbox-home 与 my-tvbox（个人 TVBox 配置，后者为空壳无站点）、huime180/4k_anime（饭太硬变体配置，新增 4K 动漫夸克接口）、wsycookie0652/zhuiju-kit（源探活看板，所列地址均已在库）、dytt123/dytt123.github.io（夸克/阿里网盘资源站，无 TVBox 配置）：

- 新增点播源 35 条：CMS 接口 0 条；配置内站点 35 条（wan7up 7 条：师兄影视、咕噜 drpy 规则，金牌、独播库、omofun日漫、Tg豆瓣、红果短剧；yangclaw 27 条：八小喵、光影、厂长、海绵、瓜子等 Guard 类爬虫站，360影视/腾讯视频/芒果TV/茶杯狐/voflix/荐片 drpy 官源规则，非凡资源；huime 1 条：4K动漫A夸克解析）。另有 51 条已有点播源补记了新出现的配置文件名；新增 spider 记录 1 条（huime 的 4K 动漫 jar）。现存 16332 条。
- 新增 TVBox 配置 5 个：wan7up tvbox.json（27 站）与 urls.json（多仓指针，8 个上游均为已入库的已知源，不再二波抽取）、lebond index.json（4664 站聚合）、yangclaw tvbox.json（40 站）、huime 4k_anime_with_fty.json（50 站，含 4K 动漫夸克接口）。现存 664 个。
- 成人内容清理：lebond 聚合为原始未筛选转储，首轮批量抽取 3201 条时发现委婉命名成人站漏网（少女、性吧、黑木耳、九一、水蜜桃、18禁、sex8、索尼 suonizy.com、淫水機 xrbsp、javday 等），已全部回滚撤销，本轮不从 lebond 批量抽取站点，只收其配置地址（用户加载聚合配置可直接使用）；待后续对其中 CMS 逐个做分类表探活筛查后再议。并入时另跳过成人名站点 4 条、成人 api 1 条、成人 URL 1 条（爱坤 ikunzyapi、立播 Libvio、乐播、番禺 fhapi9 等均未收）。
- 跳过：新探 CMS 11 个全部不通过（淘片死链、虎牙 400、光速/红牛/新浪不可达、奥斯/大众/仓库成人分类、4000/88/老鸭非 CMS）；并入时跳过 53 条已在库、18 条相对 ext、5 条本轮探活失败；硬核指南页 12 个非库内地址此前已探过不通过（摸鱼儿、饭太硬、宝盒、肥猫等为 HTML 落地页或死链，jihulab ymshaoer 实为 PNG 图片，极客小盒为十六进制加密配置，bls.json 仓库已被封禁），本轮不再重复探活。GitHub 新搜的 7 个仓库中 my-tvbox 为空配置、dytt123 与 zhuiju-kit 无可并入项。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十三批合并（2026-11-16 21:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox接口、影视接口、cms采集、drpy规则、影视仓、hipy）搜 GitHub（75 个仓库，仅 2 个是上一轮没见过的：tuannh982/hipy 是 hipy 服务端代码、casarlach/hipy-website 是空仓库，均无可收配置）；12 个已知仓库的根目录与 README 均无变化；mylazily/ziyuanzhan 重新拉取最新数据（与 20:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本（已挖过，不重挖）。上轮留待本轮的 zknjjjx upstream 13 个 {"url","final","conf"} 包装文件本轮正式立为配置条目并抽取站点，共 1131 个站点；第二波 0 个地址（13 个配置均无 urls 指针）：

- 新增点播源 9 条：CMS 接口 0 条；配置内站点 9 条，全部来自南风.json（Tg豆瓣、瓜子、金牌、王子、动漫巴士、追剧吧、冬瓜动漫、pansou|fish、TgYunPan|本地）。另有 408 条已有点播源补记了新出现的配置文件名；新增 spider 记录 8 条。现存 16297 条。
- 新增 TVBox 配置 13 个：zknjjjx upstream 全部 13 个（dxawi、二月红、俊佬、南风、小盒子、摸鱼儿、王二小、老刘备、肥猫、菜妮丝、饭太硬、香雅情、高天流云）。现存 659 个。
- 成人内容清理：并入时跳过成人 host 1 条（索尼采集站 suoniapi.com，未收）、成人名站点 11 条（Libvio/SeedHub/Xxxg/小黄人等）、成人 api 2 条。
- 跳过：探活 13 个地址全部存活；并入时跳过 1122 条（已在库 576 条、相对 ext 242 条、相对 api 290 条、成人名站点 11 条、成人 host 1 条、成人 api 2 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十二批合并（2026-11-16 20:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox源、drpy、影视壳、影视播放器、tvbox配置、影视站）搜 GitHub（128 个仓库，20 个是上一轮没见过的），新发现的配置仓库：ne7359/tvurl（OK影视/TVBox 配置汇总，13 个根配置）、hy5528/tvbox（XC/my/og 及 sub 子目录）、niuber/niuber（牛虎聚合接口）、asxs123/mytvboxlist（聚合 merged.json，2535 站）、CandyMuj/ResourceInterface（TVBox 接口收集）、woshishiq1/hipy-drpy2（drpy 规则仓的 tvbox 配置）、west2008/tvbox-files；其余新发现多为播放器客户端（Mineradio、OmniPlay、爱看影视、TVIBoxTV 等）与无关项目。mylazily/ziyuanzhan 重新拉取最新数据（与 19:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本（已挖过，不重挖）。上轮留待本轮的 zknjjjx upstream 13 个 {"url","final","conf"} 包装文件已支持 conf 抽取：共 1131 个站点，对照后仅 1 条新站且为已确认成人 host（suoniapi.com）未收；5 个 IDN 原始地址（摸鱼儿、王二小、肥猫、菜妮丝、饭太硬）不在库且本机无法解析，其 conf 内站点大多已在库。本轮新发现的多仓指针配置（niuber.json 53 个 urls、0707.json 1 个 urls）当轮下探第二波，挖出 26 个地址、14 个存活：

- 新增点播源 1605 条：CMS 接口 0 条；配置内站点 1605 条（主要来自 asxs123 merged.json 1347 条、niuber tvbox/api.json 84 条、guot55 vip2.json 48 条、west2008 ok.json 37 条、hy5528 XC.json 31 条，去重后）。另有 1519 条已有点播源补记了新出现的配置文件名；新增 spider 记录 9 条。现存 16288 条。
- 新增 TVBox 配置 40 个：第一波 32 个（ne7359 十三个根配置 0707/0821/0825/0826/0827/367/9918/99188/XYQ/dianshi/fty/jsm/js.json、hy5528 XC/my/og.json 与 sub/vod/x/pd/M.json、niuber niuber.json 与 tvbox/api.json、asxs123 merged.json、CandyMuj candymuj1.json、hipy-drpy2 box/aa/fun/jsm/test/wv.json、west2008 ok.json），第二波 8 个（niuber TVBoxOSC api.json、play.iptv365.org 小虎斑 api.json、qirenzhidao fongmi.json 与 drjs_config.json、13413.kstore.space changqing.json、szyyds x.json、xhztv 动漫频道 api.json、17264.kstore.space 哈基米.png、qirenzhidao tv.json；另有 5 个 gh-proxy 镜像记为已有 raw 条目的 mirror_url：XYQTVBox/vip2/js/000/api.json）。现存 646 个。
- 成人内容清理：CandyMuj candymuj18.json（44/72 站点为成人名）整配置未收；并入时跳过成人 host 33 条、成人名站点 175 条、成人 api 8 条、成人 URL 5 条、成人 ext host 1 条；上游 conf 抽取出的唯一新站 suoniapi.com（已确认成人 host）未收。
- 跳过：第一波探活 39 个地址：存活 32 个配置、死链 3 条（pandown.pro 连接中断、s3a.abber.cn 超时、xhww.fun DEMO 404）、受限 1 条（jihulab ok.txt 401）、reachable 3 条（hy5528 list.json 与采集静态1.json 非对象、DJyyyyw.json 无 sites/urls）；第二波探活 26 个地址：存活 14 个配置、死链 7 条（饭太硬/王二小/肥猫/菜妮丝/盒子迷/英格里希嗷呜 6 处 IDN 域名本机无法解析、fmys.top 404）、受限 2 条（jihulab xzvip.json 403、cnb.cool tvbox.json 403）、HTML 落地页 1 条（bp.tvbox.cam）、reachable 2 条（your smile66 XC.json gh-proxy 变体非对象、jihulab ymshaoer 非 JSON）；并入时跳过 4952 条（已在库 3084 条、相对 ext 555 条、相对 api 1042 条、成人名站点 175 条、成人 host 33 条、成人 api 8 条、成人 URL 5 条、无 api 10 条、api 异常 12 条、整配置多为成人 2 个、成人 ext host 1 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第三十一批合并（2026-11-16 19:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（影视源、猫影视、影视接口、影视仓、TVBox接口、影视大全）搜 GitHub（97 个仓库，14 个是上一轮没见过的），新发现：chendi0207/my-TVBOX（151★，TVBox 接口收集）、dxyc0922/Tvbox4.x_api（适配安卓 4.x 的接口）、fengy333/qist-box（自动获取 tvbox 接口）、shenzengquan/tvbox-clean（自动净化的 TVBox 接口，每日更新）、TANGZHUCC/tvbox-config（自维护接口管线）、lee-905/Lee-XFYIR-588、zknjjjx/tvbox（每日自动汇集：妞妞/多仓/cmstv）、laoliu770/tvbox-api；FanchangWang/tvbox_config 已在库；其余多为播放器客户端与无关项目。上轮留待本轮挖的两个多仓指针配置（noimank tvboxmuti.json 14 个 urls、xianyuyimu 一木多线路.json 19 个 urls）已挖：29 个非空地址里 14 个已在库，其余多为死链/受限（饭太硬三个 IDN 域名本机无法解析、pandown.pro 与 gitdl.cn 连接中断、tv.nxog.top 403、wya6.cn 456），0 新增。网页搜索补新地址（硬核指南影视仓/TVBox 列表、360doc、LibreTV 实测清单）；mylazily/ziyuanzhan 重新拉取最新数据（与 18:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本（已挖过，不重挖）：

- 新增点播源 1332 条：CMS 接口 0 条；配置内站点 1332 条（主要来自 laoliu770 tvbox.json 883 条、zknjjjx niuniu.json 185 条、YuanHsing meow.json 170 条、dxyc0922 接口-remote.json 64 条、zknjjjx cmstv.json 26 条、lee-905 tvbox.json 3 条、chendi0207 fty.json 1 条，去重后）。另有 2398 条已有点播源补记了新出现的配置文件名；新增 spider 记录 4 条。现存 14683 条。
- 新增 TVBox 配置 23 个：第一波 20 个（chendi0207 本地仓.txt、fty.json、肥猫.json、tv.菜妮丝.json、dxyc0922 接口.json、接口-remote.json、fengy333 fty.json、api.json、dianshi.json、jsm.json、shenzengquan tvbox.json、tvbox.min.json、lee-905 tvbox.json、zknjjjx cmstv.json、multi.json、niuniu.json、tvbox.json、laoliu770 tvbox.json、0619多线.txt、YuanHsing meow.json），第二波 3 个（ghfast.top 代理的 chendi0207 三文件地址）；niuniu.json 的 jsdelivr 地址记为已有 raw 条目的 mirror_url，不再单独立条。现存 606 个。
- 成人内容清理：看看资源 f-1.cc 探活存活但首屏分类/标题全是成人内容，未收；并入时跳过成人名站点 101 条、成人 host 35 条、成人 api 21 条、成人 URL 8 条。另：网页搜索提到的光速/极速/新芒果/厂长/必发 CMS 与星夜 xyezy.com——前五者已在库，星夜是已确认的成人 host，不收。
- 跳过：第一波探活 76 个地址：存活 20 个配置、死链 26 条（饭太硬三处 IDN、pandown.pro、gitdl.cn 三处、52bsj 两处、meowcf、xhww DEMO、8.210.232.168 xc.json 等连接中断，lyyyytv、mpanso DEMO、甜蜜.json 三处 404，wya6.cn 两处 456，gh.llkk.cc 522，宝盒接口.top IDN，半糖仙人 423）、受限 2 条（tv.nxog.top 403、gitlab ygbh.json 403 跳登录）、HTML 落地页 7 条（weixine.net 跳 julydns 停放页、八仙多仓、tv.xn--yhqu5zs87a.top、agit.ai 两处、yydsys.top 跳首页、摸鱼儿）、reachable 20 条（zknjjjx upstream 13 个是 {"url","final","conf"} 包装、站点在 conf 里暂未抽取，fengy333 课堂 json 5 个是课程分类数据不是 TVBox 配置，TANGZHUCC config/tvbox.json 是空模板 sites 为空，gh-proxy 的 XC.json 返回非对象）、CMS 1 个为成人内容；第二波探活 41 个地址（从 0619多线.txt 的 108 条地址与 zknjjjx multi.json 的 14 个 urls 挖出）：存活 4 个（均为第一波已收配置的镜像）、死链 24 条、受限 2 条（jk.catvod.site 403、9877.kstore.space sun.json 403）、HTML 落地页 4 条、reachable 7 条；并入时跳过 4596 条（已在库 3631 条、相对 ext 534 条、相对 api 266 条、成人名站点 101 条、成人 host 35 条、成人 api 21 条、成人 URL 8 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。
- 留待下轮：zknjjjx upstream 13 个文件是 {"url","final","conf"} 包装（站点在 conf.sites 里），其中 5 个原始地址不在库且为 IDN 域名（摸鱼儿、王二小、肥猫、菜妮丝、饭太硬，本机无法解析）；下轮可考虑支持 conf 包装抽取。另：库里“量子”站两条近乎重复的记录仍是历史遗留，未擅自合并。

## 第三十批合并（2026-11-16 18:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（影视app、苹果CMS、影视仓库、CMS采集、影视聚合、短剧）搜 GitHub（122 个仓库，75 个是上一轮没见过的），新发现：nonoyesyes/yingzhou-source-hub（源仓 feed，160 条配置清单）、passionsu-su/TVbox（配置导航与检测仓库，66 条候选配置目录）、xxx0139/yingshijuhe、Silencecavalier/iread-plugins（cmstv 苹果CMS 聚合规则）、z1859741z-stack/vplay（7 个 CMS 接口）；其余多为短剧制作工具与播放器客户端，没有可直接收录的配置地址。网页搜索补新地址（硬核指南、360doc：天神IY、jundie top98、dxawi 0.json 等）；mylazily/ziyuanzhan 重新拉取最新数据（与 17:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本（已挖过，不重挖）：

- 新增点播源 1448 条：CMS 接口 0 条；配置内站点 1448 条（主要来自 DRjopper 231016.json 678 条、xiaoya.json 118 条、xpg.json 80 条、南风.json 62 条、m.json 55 条、tvbox.json 54 条、天神.json 46 条、幸福年年.json 36 条等，去重后）。另有 1673 条已有点播源补记了新出现的配置文件名；新增 spider 记录 27 条。现存 13351 条。
- 新增 TVBox 配置 70 个：yingzhou feed 的 52 个（gaotianliuyun XYQ.json、qist 367/dianshi/jsm.json、1771245847 六文件、Lightconer 单仓聚合.json、DRjopper 231016.json、a736240087 1/2.json、youhunwl 六个 txt 配置、zxzxzh tvbox/xiaoya.json、jifeng250 四文件、fswws 两文件、CandyMuj candymuj.json、chitue js/py.json、coderzcr tv.json、Huameng11 tvbox.json、JianghaoPi aggregate.json、liu673cn vod 四文件、lubin776 备份十三文件、xuanjinok TV.json）、passionsu 目录的 16 个（kimwang1978 七文件、vito-xu config.json、xianyuyimu 四文件、wuli007 config.json、noimank tvboxmuti.json、jinenge tvbox.json、hackyjso config_open99.json）、指针挖掘的 2 个（FongMi CatVodSpider config.json、mcp2016 pj.json）。现存 583 个。另：Lightconer 4k.json 的 jsdelivr 地址记为已有 raw 条目的 mirror_url，不再单独立条；网页搜索的 8 个地址本轮 0 新增（天神IY、700sjro44343、jundie top98、dxawi 0.json、jihulab tongyong.json 五个已在库，8.210.232.168 xc.json 与 xhww.fun DEMO.json 死链、agit.ai prox.json 为 HTML 落地页）。
- 成人内容清理：3 个 CMS（360 资源站、越南资源站、索尼采集站）探活存活但均为成人站未收；并入时跳过成人名站点 62 条、成人 host 28 条、成人 api 17 条、成人 URL 1 条、CMS 成人 host 2 条；vplay 清单里的 360zy.com 与 iread 的魔都站已在库或为成人站，未新增。
- 跳过：探活 93 个地址：存活 71 个配置 + 3 个 CMS（均为成人站未收）、死链 5 条（syzsky config.json、fish2018 all.json、PyramidStore py.json 三处 404，8.210.232.168 xc.json 与 xhww.fun DEMO.json 连接中断）、受限 2 条（tvbox.wushui.fun 与 9877.kstore.space sun.json 403）、HTML 落地页 1 条（agit.ai guot54 prox.json）、reachable 11 条（cat/js config_open 系列与 Lightconer sources.json、zongchenghuan site.json 等是 JSON 但无 sites/urls 键、jihulab ymz1231 非 JSON）；本轮无存活 .txt 多仓文件（youhunwl 六个 .txt 实为 JSON 配置）、第二波 0 个地址；并入时跳过 4269 条（已在库 3062 条、相对 ext 734 条、相对 api 311 条、成人名站点 62 条、成人 host 28 条、成人 api 17 条、无 api/格式问题 7 条、成人 URL 1 条、CMS 成人 host 2 条、地址格式/内网问题 45 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。
- 留待下轮：本轮存活的两个多仓指针配置（noimank tvboxmuti.json 14 个 urls、xianyuyimu 一木多线路.json 19 个 urls）留待下轮挖。另：库里“量子”站有两条近乎重复的记录（同一归一化 api，末尾斜杠不同，type 均为 1），是历史遗留，本轮只在其中一条上补记了新配置文件名，未擅自合并。

## 第二十九批合并（2026-11-16 17:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（libretv、TVBox配置、drpy2、xbpq、影视盒子、影视仓）搜 GitHub（89 个仓库，44 个是上一轮没见过的），新发现：longge83/tvbox-merged（每日自动探活合并的多版本聚合配置）、thqPrivateRepo/tvbox-dc（多仓配置合集，共 93 条）、JinRudy/tvbox-more、193881/tvbox-config、zhangxiansheng070422/tvbox-config、royzhu36/TVBoxConfig、Yanjiehh/tvbox-sources、tvbox342078879/probe-lines（XBPQ ext 直链验活源）、ailin5204/tvbox_share_new、1599304510-jpg/tvbox-config，及五家新的 LibreTV 源清单（hthyeah、bandy2023、Simon8806、poor-admin、huangxin0512）；libretv 关键词多数命中客户端 fork，不是源清单。网页搜索补新地址（硬核指南、360doc：liu673cn m.json、freed.yuanhsing meowcf.json、pastebin、jihulab boxtvv YSDQ.json）；mylazily/ziyuanzhan 重新拉取最新数据（与 16:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本（已挖过，不重挖）：

- 新增点播源 1159 条：CMS 接口 0 条；配置内站点 1159 条（主要来自 longge83 tvbox.json 与 tvbox-full-homefirst.json 各 1513 站、thqPrivateRepo mybox.json 514 站、longge83 tvbox-home.json 429 站、tvbox-quality.json 218 站、ailin5204 tvbox.json 78 站、clun.top fun.json 87 站等，去重后）。另有 3170 条已有点播源补记了新出现的配置文件名；新增 spider 记录 11 条。现存 11903 条。
- 新增 TVBox 配置 26 个：longge83 六文件（tvbox/tvbox-full-homefirst/tvbox-stable7/tvbox-quality/tvbox-cn-fast/tvbox-home）、JinRudy tvboxmuti.json/tvboxvod.json、193881 tvboxconfig.json/duanju.json、zhangxiansheng api.json/config.json、royzhu36 tvbox.json、Yanjiehh 360.json、thqPrivateRepo dc.json/dc_fast.json/mybox.json、1599304510-jpg tvbox.json、ailin5204 tvbox.json、clun.top fun.json、7337.kstore.space 测试勿传、17264.kstore.space 豆包.jpg、ysys.lic10.cn ys、8492.kstore.space 超玩家 ncwj、ghfast sylvan97 index.json 与 qist 0821.json。现存 513 个。1014_fix.json（36/61 成人名）整配置未收。
- 成人内容清理：360zy.net 与 360zy.com 是同一站（总数同为 75212、首屏标题相同），一度被误收为 CMS，已删除，域名与地址已进成人黑名单；“360|弹幕”（csp_HBcms10CAT，ext 指向 360zy.com）也已删除——合并脚本的成人检查只看 api 不看 ext，已修复（ext 同样查成人 host 与 URL 黑名单）；360zyzz.com、360zy.tv、vnzyz.com 是已确认成人站的同站变体域名，后续只拦截新增条目，库里已有的 7 条旧条目按 14:06 先例保留不动。越南资源站 vnzyz 分类表仍是丝袜美腿/盗撮未收；索尼采集站 suonizy 探活为成人内容未收；360zy.com 的 CMS 未收。另：raw 直链的 refs/heads 变体地址今后记为规范直链 + 镜像，不再单独立条（脚本已修）。
- 跳过：探活 94 个地址：存活 27 个配置 + 3 个 CMS（均为成人站未收、另 1 个成人内容）、死链 34 条、受限 5 条、HTML 落地页 10 条、reachable 13 条；本轮无存活 .txt 多仓文件，第二波 0 个地址；并入时跳过 3942 条（已在库 3446 条、相对 ext 262 条、相对 api 99 条、成人名站点 104 条、成人 host 18 条、成人 api 7 条、成人 URL 2 条、整配置多为成人 2 个、无 api/格式问题 1 条、CMS 成人 host 1 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十七批合并（2026-11-16 15:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（catvod、cms采集、影视采集、tvbox源、影视仓订阅、影视站）搜 GitHub（110 个仓库，74 个是上一轮没见过的），新发现：YiMing918/ym-tvbox（4 星，220 站、每日 05:30 自动探活合并）、smallniangao/tvbox（6.180189.com 订阅端点）、707214981/tvbox-sources（TVBox PY 源）、tarynwyj/yingshicang-confi-self（影视仓/TVBox 多仓订阅合集）、guxia66898/tvbox-static（drpy 静态订阅）、daletyler1737/tvbox-sources（多仓+单仓订阅）、efefsdwd/tvbox-sub（5 个公开苹果 CMS + 精选直播）、fenghao0/tvbox-config（验活后的采集源列表）、YH-Music/vod-sources（路由器机器人维护的苹果 CMS 清单 vod.b64，10 条接口全部已在库）；网页搜索补新地址（360doc 教程页：52bsj wuai/xiaohu、gitlab ygbh1、ZTHA000 djk1/gyckname）；mylazily/ziyuanzhan 重新拉取最新数据（74/62/20 条，与 14:06 相比 0 条新站），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本；本轮新发现的多仓配置（tarynwyj multi/multi-vod、daletyler multi）里的 urls 指针当轮下探，又挖出 qist fty.json/xiaosa api.json/0821.json、gaotianliuyun 0825.json/0821.json、mrgaoshuiquan tvbox.json、dxawi 0.json、544609136 vod_slim/vod_full.json、sylvan97 index.json/lite.json、Lightconer ouge.json/feimao.json、zhuzhuyule tvbox.json 共 17 个地址：

- 新增点播源 491 条：CMS 接口 0 条（360 资源站命中成人 URL 黑名单未收；越南资源站 vnzyz 分类表全是丝袜美腿/盗撮，在候选阶段已排除；索尼采集站 suonizy 探活为成人内容未收）；配置内站点 491 条（主要来自 707214981 tvbox.json 287 站、YiMing918 peter_tvbox_pro.json 219 站、zhuzhuyule tvbox.json 228 站、gaotianliuyun 0825.json 135 站、qist xiaosa api.json 116 站等，去重后）。另有 234 条已有点播源补记了新出现的配置文件名；新增 spider 记录 7 条。现存 9611 条。
- 新增 TVBox 配置 19 个（净增）：YiMing918 peter_tvbox_pro.json、707214981 tvbox.json、tarynwyj multi.json/multi-vod.json、guxia66898 config.json、daletyler multi.json/oktv-fixed.json、fenghao0 tvbox-cinenest-ok.json（gist 直链）、efefsdwd tvconfig.json、smallniangao 6.180189.com 订阅端点、qist fty.json/xiaosa api.json/0821.json、gaotianliuyun 0825.json/0821.json、mrgaoshuiquan tvbox.json、dxawi 0.json、544609136 vod_full.json、sylvan97 index.json/lite.json、zhuzhuyule tvbox.json（以上 gh-proxy 包裹的均改记为 raw 直链 + 镜像，不再单独立条）；Lightconer ouge.json/feimao.json 的 jsdelivr 地址记为已有 raw 条目的 mirror_url。现存 421 个。
- 成人内容清理：544609136 vod_slim.json 54 站里 37 站成人名（黑料/桃花/大奶子/成人06/奶香/辣椒/森林/老色/黄仓/番号/souav 等），整配置多为成人——站点一条未收，配置地址也不进公开配置表（已从本轮合并结果里去掉）。360zy 首屏分类现为国产剧/爽文短剧，但 14:06 分类表实测伦理片 1641 条的结论不变，继续按成人 URL 黑名单拦截；vnzyz 分类表仍是丝袜美腿/盗撮；suonizy 命中成人 URL 黑名单。三站均未收。
- 跳过：探活 37 个地址：存活 24 个配置（另 2 个 CMS 存活但均为成人站未收、1 个 CMS 成人内容）、死链 4 条（52bsj wuai/xiaohu、box.ufuzi 短剧频道、fty.xxooo.cf 远端断开）、受限 2 条（gitlab ygbh.json 403 跳登录页、tv.nxog.top 403）、HTML 落地页 2 条（ghproxy ZTHA000 djk1/gyckname 跳 ghfast.top）、reachable 2 条（tarynwyj config.json 与 config-test.json 只有直播、没有点播源，按 VOD-only 规则不收）；探活前去重：YH-Music 10 条 CMS 全部已在库、mylazily 0 条新站、IDN 域名（肥猫.net、punycode 域名）不探；并入时跳过 1215 条（已在库 832 条、相对 ext 199 条、相对 api 100 条、成人名站点 54 条、成人 host 24 条、成人 api 4 条、CMS 成人 URL 1 条、整配置多为成人 1 个）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十六批合并（2026-11-16 14:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox订阅、影视源、drpy、猫影视、影视接口、tvbox json、影视仓配置、点播源）搜 GitHub（65 个仓库，12 个是上一轮没见过的），新发现：wokaotianshi123/jgcj（23 星，影视站之家采集接口合集，7 个文件同为 57 站不同应用格式）、yujuanIt/TVSources（居安影院公开源站：点播、TVBox 配置与直播分模块维护）；网页搜索补新地址（硬核指南影视仓页、viptv 配置表、MacCMS 文档的采集接口、影视站长圈厂长资源、星夜资源站）；mylazily/ziyuanzhan 重新拉取最新数据（74 条，57 条状态正常），applecms-sources 与追剧资源本轮仍 404、沿用 1206 的副本；上轮遗留跟进：vgmr-99 备份索引里的南风指向 yoursmile66/TVBox 的 XC.json（直链 raw 已探活）、xhztv dc 多仓指针下探出 9 个新配置地址：

- 新增点播源 308 条：CMS 接口 0 条（越南资源站 vnzyz 分类表全是丝袜美腿/盗撮未收；星夜资源站 xyezy 分类表是强奸乱伦未收；索尼采集站 suonizy 命中成人 URL 黑名单未收）；配置内站点 308 条（主要来自居安 vod-sites.json 250 站——432 站清单去重后、jgcj 七文件、hgyx.json）。另有 350 条已有点播源补记了新出现的配置文件名；新增 spider 记录 1 条（hgyx.json 的 jar）。现存 9130 条。
- 新增 TVBox 配置 12 个：hgyx.json、居安 box.json/vod.json/warehouse.json/vod-sites.json、jgcj 七文件（zcying/zyvying/zytvbox/ysdqbox/zypcbox/libretv/hongguo，同一批 57 站的七种应用格式）。现存 402 个。南风 XC.json 清理：库里原有两条代理地址（ghproxy.net、agit.ai），本轮直链 raw 已探活，改记为 raw 条目 + ghproxy.net mirror_url，不再重复立条。
- 成人内容清理：本轮按 CMS 分类表实测发现 5 个成人站——suoniapi.com 与 suonizy.net（伦理/港台三级/韩国伦理/西方伦理/日本伦理/两性课堂/写真热舞）、360zy.com（伦理片分类实测有 1641 条视频）、xyezy.com（强奸乱伦）、api.vnzyz.com（丝袜美腿/盗撮），其 6 条精确地址已加入成人 URL 黑名单、域名已记入成人 host 表（后续轮次自动拦截）。库里已有的 10 条（索尼 4 条、360 6 条）按 08:06 批的先例全部删除（清单见本地 hourly/adult-purge-2026-11-16-1406.json），现存 9120 条。教训：只看站点名会漏检——“360资源”“索尼资源”名字正常，但分类表里有伦理/三级分类，本轮起新增 CMS 与配置内站点同时检查 api 域名是否命中成人 host 表；成人词表补“强奸/乱伦/调教/内射/痴汉/迷奸/凌辱/偷拍/露出/中出/口交/自慰/援交/萝莉/巨乳/擦边”。
- 跳过：探活前去重 10 条（已在库 5 条、IDN 域名不可请求 4 条，另有 1 条直播 M3U 签名地址按 VOD-only 规则不探）；探活 35 个地址（含 jgcj 的 raw 直链重探）：存活 14 个（配置 12、CMS 2，CMS 均为成人站未收）、死链 12 条（jgcj 的 7 个 worker 地址全部 404——README 里的 a.wokaotianshi.eu.org 链接已失效，改用仓库 raw 直链；dp.sxtv、meowtv、100km、甜蜜 raw.iqiq.io 远端断开）、受限 3 条（acwing jsm.json 403、kstore nzk 401、jihulab xzvip 403 跳登录页）、HTML 落地页 3 条（bp.tvbox.cam、agit.ai 龙门影视与巧技）、reachable 2 条（极客小盒 gh-proxy.org 与月光宝盒 jihulab 均为十六进制加密配置、无法读取不收）；jgcj 的 5 个文件初探为“非对象 JSON”，重探后确认为裸列表/tbl_site/api_site/影视大全四种格式，已适配抽取；并入时跳过 515 条（已在库 354 条、成人名站点 122 条、成人 host 19 条、相对 ext 15 条、成人 api 2 条、CMS 远端不可达 2 条、无 api 1 条）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十五批合并（2026-11-16 13:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（影视仓、tvbox接口、影视订阅、drpy规则、猫影视接口、tvbox配置源、点播接口、影视资源站）搜 GitHub（61 个仓库，30 个是上一轮没见过的），新发现：hubeizgd1979/tvbox-merge（8 星，每 4 小时重建核查，config_all.json 早已在库，389 站）、longer519/tvbox（老盒子 Android 4.4 专用配置）、vgmr-99/tvbox-api-backup-mirror（lubin776 的每日同步镜像）；网页搜索补新地址（硬核指南影视仓页面）；mylazily/ziyuanzhan 重新拉取最新数据，applecms-sources 与追剧资源本轮 404、沿用 1206 的副本；上轮多仓指针继续下探：网络名家.txt 指向 21 个 play.iptv365.org 作者配置、fm.json 指向南风/巧技/采妮丝、PizazzGY 指向影视/磁力/云盘_api.json；adminouyang 饭太硬目录与点播源目录通过 GitHub 连接器列出确认（点播源 14 个 txt 文件齐全）：

- 新增点播源 588 条：CMS 接口 0 条（越南资源站 vnzyz 分类表全是丝袜美腿/盗撮未收；索尼采集站 suonizy 命中成人 URL 黑名单未收）；配置内站点 588 条（主要来自 api.json 308 站——iptv365 二十余个作者配置与安忆 api.json、欧歌.txt 56 站、PizazzGY 影视_api.json 52 站、Moew.txt 41 站、肥猫.txt 26 站、easytv.jpg 23 站等）。现存 8822 条。另有 677 条已有点播源补记了新出现的配置文件名；新增 spider 记录 16 条；PizazzGY 三文件与 longer519 config.json 的代理/jsdelivr 镜像改记为新增 raw 条目 + mirror_url，不再单独立条。
- 新增 TVBox 配置 32 个：iptv365 的 21 个作者配置（饭太硬/小米/肥猫/菜妮丝/王二小/摸鱼儿/PG/欧歌/潇洒/天微/天天开心/香雅情/南风/骚零/白嫖/OK/戏曲音乐/短剧频道/少儿频道/动漫频道/iptv365）、PizazzGY 三文件（影视/磁力/云盘_api.json）、longer519 config.json、vgmr-99 list.txt（备份索引）、adminouyang 饭太硬.txt、星微 测试勿传、easytv.jpg、安忆 api.json、xhztv dc、pastebin gtbKvnE1。现存 390 个。
- 跳过：探活前去重 21 条（已在库 15 条、IDN 域名不可请求 3 条、候选内重复 2 条、上轮已探 HTML 落地页 1 条）；探活 59 个地址：存活 36 个（配置 34、CMS 2，CMS 均为成人站未收）、死链 14 条（moeyy 代理 5 条远端断开、巧技/采妮丝远端断开、52bsj 两处远端断开、meowcf/xhww DEMO 远端断开、南风 XC.json 404、gitee 半糖仙人 423）、reachable 1 条（vgmr-99 config.json 无 sites/urls 键）、受限 1 条（gitlab ygbh.json 403 跳登录页）、HTML 落地页 7 条（xn--cnq85d、yydsys duo、agit.ai、摸鱼儿、124.71.19.220、xhztv.pro、ghproxy ZTHA000 djk1 跳 ghfast.top）；并入时跳过 2288 条（已在库 1573 条、相对 ext 383 条、相对 api 212 条、成人名站点 81 条、api 命中成人词 9 条、成人 URL 精确命中 2 条、CMS 成人 URL 1 条、整配置多为成人 1 个、配置无法解析 1 个、配置已在库 13 条、无 api 1 条、内网/无效 api 9 条、镜像已记录 1 条）。
- 修复：6 个 adminouyang 点播源 txt 配置（Moew/小米/挺好/欧歌/肥猫/骚零）自 08:06 起因手写 JSON 宽松语法无法解析、站点一直未抽取，本轮用宽容解析器重新抽取，共收回 141 站（欧歌 56、Moew 41、肥猫 26、挺好 21、小米 14、骚零 8）；其余 7 个 txt 配置重新抽取无新增（站点已在库，仅补记配置文件名）。代理镜像识别扩展：github.moeyy.xyz、mirror.ghproxy.com、ghproxy.cc、g.blfrp.cn 包裹的 raw 地址现也识别为镜像；无 raw 条目的镜像改为新增 raw 条目 + mirror_url（PizazzGY 三文件、longer519 config.json）。成人词表补 "madouse/madou/feichai"（魔法 madouse.la、废柴 fhapi9.com 漏网，量子/非凡是非成人 CMS 保留）。南风 XC.json 在 adminouyang 仓库已 404（南风目录不存在），moeyy 代理同时失联，本轮未收；vgmr-99 备份索引里南风指向 yoursmile66/TVBox 的 XC.json（ghproxy.monkeyray.net 代理），留待下轮探活；xhztv dc 多仓指针（PG 线路、影视仓、神仙线路、俊于、玄珠等）同样留待下轮逐批探活。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十四批合并（2026-11-16 12:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox配置、影视源、drpy、猫影视、影视接口、cms采集、苹果cms、tvbox源）搜 GitHub（70 个仓库，60 个是上一轮没见过的），新发现：25175/tvyuan（132 星，每小时自动聚合）、adminouyang/231006（258 星，搜集 tvbox 配置）、deli6250/tvbox-config、xiaopeng-97/my-tvbox（每日健康检查重建）、hubeizgd1979/tvbox-config、huangshaoze37-tech/hotel-tv；网页搜索补新地址（硬核指南的配置列表）；mylazily/ziyuanzhan、applecms-sources 与追剧资源重新拉取最新数据：

- 新增点播源 1817 条：CMS 接口 0 条（越南资源站 vnzyz 与索尼采集站 suonizy 均为成人站未收）；配置内站点 1817 条（主要来自 heroaku_ayn 455 站、heroaku_ptest 442 站、yuan2.txt 285 站、heroaku_dtes 215 站、heroaku_pyn 135 站、adminouyang 的 XYQ.json 107 站等）。现存 8234 条。另有 2466 条已有点播源补记了新出现的配置文件名；新增 spider 记录 8 条；同一配置文件的代理/jsdelivr 镜像改记为 mirror_url，不再单独立条（hubeizgd1979、hotel-tv 各 1 条）。
- 新增 TVBox 配置 25 个：heroaku 四文件（宽容解析器修复后成功抽取）、25175/tvyuan 的 cc0cd.cc.cd 直链（1462 站）、xiaopeng-97 的 4 个 dist 配置（每日健康检查）、hubeizgd1979 的 dist/config.json、hotel-tv 的 tvbox.json（8 站）、adminouyang 的 12 个（FM/fm.json、PizazzGY、XYQTVBox.txt、gao 的 0821/0822/0826/XBPQ/XYQ、js.json、ouge/111.json、网络名家.txt、点播源/CandyMuj.txt）、szyyds.cn 的 x.json（62 站）、xhztv 的 4k.json（53 站）。现存 358 个。
- 跳过：探活前去重 35 条（已在库 28 条、IDN 域名不可请求 3 条、上轮已探非存活 4 条）；探活 37 个地址：存活 30 个（配置 28、CMS 2，CMS 均为成人站未收）、死链 5 条（tv.cc0cd.cc.cd 的 /jj 与 /multi 502、9xi4o.tk 的 0725.json 远端断开、yc.wya6.cn 456、半糖仙人 gitee 423）、reachable 1 条（deli6250 的 config.json 只有直播、没有点播源）、HTML 落地页 1 条（itv666 的 config.webp 跳回首页）；并入时跳过 3253 条（已在库 2649 条、成人名站点 143 条、相对 ext 312 条、相对 api 137 条、api 命中成人词 4 条、成人 URL 精确命中 2 条、CMS 成人 URL 1 条、镜像同内容 3 条、镜像已记录 1 条、配置已在库 1 条）。
- 修复：heroaku 四文件因 `#` 章节标题行与缩进 `//` 注释行导致 JSON 解析失败，本轮起探活与合并共用宽容解析器（去注释行/BOM/尾逗号/控制字符，逐个抽取 sites 对象兜底），四文件全部收回；szyyds 的 x.json 带 BOM、xhztv 的 4k.json 含行内注释分隔线，同法修复；gh-proxy 包裹地址请求时需保留 `:` 与 `@` 不编码，否则会 404（本轮曾因此误判 3 个镜像死链，已修正重探）；上轮待办 yuan2.txt 的站点本轮已抽取（285 站），其 spider 记录也已补记。deli6250 的 config.json 只有直播、没有点播源，按 VOD-only 规则不收。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十三批合并（2026-11-16 11:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮用新关键词（tvbox接口、影视仓、cms接口、drpy规则、影视聚合、xbpq、免费影视、影视资源站）搜 GitHub（26 个仓库，16 个新发现），其中 cluntop/tvbox（OK影视，695 星）6 个配置文件与 andywe0921-ops/applecms-sources（18 个 CMS 站自动更新）是新发现；网页搜索补新地址；mylazily/ziyuanzhan 与 applecms-sources 重新拉取最新数据；上轮 hkuc 多仓指针继续下探：tv/0–tv/6 各目录的同名镜像文件只留 raw 版 tv/6 一份（去重 114 条同文件跨目录/代理重复地址）：

- 新增点播源 552 条：CMS 接口 0 条（越南资源站 vnzyz 分类表仍含丝袜美腿/盗撮栏目未收；索尼资源站 suonizy 首页翻页出现“日本伦理”分类，探针首 5 条未命中，合并时被误收随后已移除并写入成人 URL 黑名单）；另清理往期漏网的同站旧条目 1 条（💕越南(直连)，vnzyz.com，与 api.vnzyz.com 同站，分类全为丝袜美腿）；配置内站点 552 条（主要来自 hkuc 的 js.json 186 站、liu673cn_m.json 142 站、0825.json 102 站、0821.json 36 站、XYQ.json 24 站、Dong-learn9_tvbox2.json 20 站，cluntop 的 aa.json 18 站、jsm.json 15 站等）。现存 6417 条。另有 209 条已有点播源补记了新出现的配置文件名；新增 spider 记录 5 条。
- 新增 TVBox 配置 16 个：hkuc tv/6 的 8 个新文件（0821/0825/0826/0827、Dong-learn9_tvbox2、XYQ、js.json、liu673cn_m.json；0828/XBPQ 上轮已确认 404，heroaku 四文件 JSON 语法错误仍未收）、xyq254245 的 XYQTVBox.json（allproxy 代理地址）、cluntop/tvbox 的 6 个配置（box.json、aa.json、fun.json、jsm.json、wv.json、test.json）、GaiVmao 的 yuan2.txt（529 行，内容为带注释的 JSON 配置，因一处语法错误站点未抽取，地址已收录）。现存 333 个。
- 跳过：探活前去重 143 条（hkuc 同文件跨目录/代理重复 114 条、已在库 11 条、IDN 域名不可请求 7 条、hkuc 已在库文件 7 条、上轮已探非存活 3 条、候选内重复 1 条）；探活 38 个地址：存活 18 个（配置 16、CMS 2，CMS 均因成人未收）、死链 3 条（ZTHA000 的 djk1.json 404、52bsj 小虎、菜妮丝远端断开）、reachable 9 条（200 但非配置 JSON，如 heroaku 四文件语法错误、yoursmile66 XC.json 与月光宝盒多余数据、pastebin 与 xhztv dc 编码/格式问题）、受限 1 条（gitlab ygbh.json 403 跳登录页）、HTML 落地页 7 条（ZTHA000 两个 gh-proxy 地址跳 ghfast.top、yydsys duo、龙门影视 agit.ai、摸鱼儿、影仓 124.71.19.220、xhztv.pro）；并入时跳过 748 条（已在库 449 条、相对 ext 139 条、相对 api 86 条、成人名站点 58 条、无 api 8 条、内网/无效 api 5 条、api 命中成人词 2 条、配置无法解析 1 条）。
- 教训：探针只看 CMS 首页前 5 条的分类会漏检——suonizy 的“日本伦理”分类在第 2 页才出现，本轮又险些误收（已移除）；已把 suonizy 与 vnzyz 的归一化地址写入成人 URL 黑名单（hourly/dl-0706/adult-url-blocklist.json），并修正黑名单写入时带尾部斜杠导致比对失效的问题，今后按归一化地址精确拦截。另：hkuc 多仓指针每层 tv/N 目录都是同一批文件的不同代理镜像，下轮起按文件名只留一份，不再逐个探活。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十二批合并（2026-11-16 10:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮主攻上轮留下的多仓指针：把 09:06 轮次探活通过的聚合配置里的 urls 指针逐批探活（44 个配置候选），另用新关键词（tvbox源、影视源、cms采集、drpy、catvod、tvbox订阅、影视接口、tvbox仓库）搜 GitHub（16 个仓库，7 个新发现）与网页搜索补新地址；mylazily/ziyuanzhan 重新拉取最新数据；上轮待办 hkuc/tvbox-config 的 tv/数字目录已枚举（7 个数字目录 tv/0–tv/6，各含 urls.json 多仓指针与约 20 个镜像配置，内容多与上游同名文件重复，本轮只取 urls.json 指针与 12 个未见过的特色镜像）：

- 新增点播源 339 条：CMS 接口 0 条（越南资源站 vnzyz 分类表仍含丝袜美腿/盗撮栏目未收；索尼资源站 suonizy 首页面分类出现“日本伦理”，本轮探活词表未命中被误收，合并后已移除）；配置内站点 339 条（主要来自 yw88075_js.json 211 站、hackyjso_jzy.json 93 站、anaer_meow.json 77 站、franksun1211_0706.json 39 站等）。另清理往期漏网的伦理站 5 条（易看资源-伦理、影库资源-伦理、酷伦理-伦理、博天堂-伦理及易看同站异名条目），净增 334 条，现存 5866 条。另有 523 条已有点播源补记了新出现的配置文件名；新增 spider 记录 3 条。
- 新增 TVBox 配置 22 个：hubeizgd1979/tvbox-merge 的 config_all.json（740 影视源，每 4 小时重建并核查有效性，gh-proxy 与直连两条地址均已收录）、tlwj01/tvbox-java-spider 的 5 个订阅 JSON（云端版 safe-subscription.json 27 站 type:3，另有 replica/replica2/replica3/pan 三批复刻订阅）、vgmr-99/tvbox-api-backup-mirror 的 config.json（lubin776/tvbox-api-backup 每日镜像）、hkuc 的 7 个 tv/N/urls.json 多仓指针与 7 个特色镜像配置（hkuc_ai、heroaku_ayn/ptest/pyn、FanchangWang_tv、anaer_meow、hackyjso_jzy、franksun1211_0706、gaotianliuyun_0707、yw88075_js 等）。现存 317 个。hkuc 的 0828.json、XBPQ.json 在 tv/0 下是 404 死链，未收；heroaku 三个文件 JSON 语法错误（reachable），未收。
- 跳过：探活前去重 33 条（已在库 17 条、IDN 域名不可请求 9 条、候选内重复 7 条）；探活 82 个地址：死链 39 条（含 hkuc 的 0828/XBPQ 404、meowcf/52bsj 远端断开、tvbox.vip/4k 404）、reachable 8 条（200 但非配置 JSON，如 heroaku 三文件语法错误、xhztv 4k.json 控制字符错误）、受限 6 条（403/429）、HTML 落地页 5 条（agit.ai 两处、itv666 的 aowu config.webp 跳回首页）；并入时跳过 1637 条（已在库 956 条、相对 api 451 条、相对 ext 141 条、成人名站点 69 条、无 api 68 条、内网/无效 api 49 条、api 命中成人词 1 条）。
- 教训：CMS 成人词表漏了“伦理”——suonizy 首页面分类“日本伦理”未被探活与合并两层词表命中，导致误收录（已移除并清理往期 4 个伦理站）；已在探活、合并、候选三处脚本的成人词表与合并层分类复核里补上“伦理”，以后同类站不再进库。IDN 域名（饭太硬、肥猫、王二小放牛娃、摸鱼儿等）urllib 无法直接请求，均按失效/落地页处理。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第二十一批合并（2026-11-16 09:06，每小时整理）

仍按用户 2026-11-16 07:02 指令只做点播（VOD-only），live/、epg/ 文件原样不动。本轮主攻上轮留下的多仓指针：把 08:06 轮次探活通过的聚合配置里的 urls 指针逐批探活（247 个配置候选），另用新关键词（tvbox接口、影视仓库、资源站、采集站、影视app、tvbox config、ziyuan、tvbox）搜 GitHub（18 个仓库）与网页搜索补新地址；mylazily/ziyuanzhan 重新拉取最新数据：

- 新增点播源 2866 条：CMS 接口 0 条（新发现的越南资源站 vnzyz 分类表含丝袜美腿/盗撮栏目、索尼资源站 suonizy 命中成人词，均未收录）；配置内站点 2866 条（主要来自 hesanyue50-lang 的聚合配置 477 站、Dong-learn9 的 tvbox1.json 388 站、qist/gao 的 js.json 298 站、liucn 的 m.json 234 站、yydf 的 yydfjk.json 193 站等）。现存 5532 条。另有 2748 条已有点播源补记了新出现的配置文件名；新增 spider 记录 36 条。
- 新增 TVBox 配置 149 个：多仓指针挖出的深层配置 148 个（含 qist 0821/0826/0827/js.json、gao 的同名四件套、FongMi CatVodSpider 的 config.json、codeberg/gitlab/gitmirror 等多家镜像线路），以及 huatong202/tvbox-custom 的 custom.json（牛虎底本定制，129 站，4K 区前置，实测可用）。现存 295 个。huatong202 的 niubihu-1.json 只是维护快照（仓库里 custom.json 才是主版）、adult.json 是成人单独版，均未收录。
- 跳过：探活前去重 288 条（候选内重复 240 条、已在库 38 条、纯直播播放列表指针 10 条）；探活 245 个地址：HTML 落地页 39 条（饭太硬、摸鱼儿、宝盒类，真实地址要从页面里再找）、reachable 30 条（200 但非配置 JSON，如 hgyx.json 语法错误）、死链 23 条（含 chendi0207 的香雅情/南风/骚零/多多四处 404、半糖仙人 Gitee 423）、受限 2 条（403）；并入时跳过 10689 条（首轮 10580 条：已在库 5326 条、相对 api 2688 条、相对 ext 2119 条、成人名站点 370 条、api 命中成人词 31 条、成人 URL 精确命中 6 条、无 api 10 条、内网/无效 api 30 条；补并 custom.json 时又跳过 109 条，其中 api 命中成人词 1 条）。
- 教训：本轮探活中途被运行时重启打断，已用“已保存正文按本地重建 + 其余重探”的方式续跑，未丢数据；含中文路径的配置地址需 percent-encode 后再请求，IDN 域名（饭太硬、肥猫、王二小放牛娃、摸鱼儿等）urllib 无法直接请求，均按失效/落地页处理；CMS 探活的成人词表比并入时窄——vnzyz 首轮被标 alive 是因为探活词表缺“丝袜/盗撮”，已在并入层加分类表复核拦截。hkuc/tvbox-config 的 tv/数字目录/urls.json 尚未枚举（未认证 GitHub API 触限 403，按规则等下一轮，不绕路）。
- 直播/EPG：按 07:02 指令未搜、未探、未并、未传，文件原样不动。

## 第十九批合并（2026-11-16 07:06，每小时整理）

本轮起按用户 2026-11-16 07:02 指令只做点播（VOD-only）：停止一切直播/EPG/成人直播的搜索、探活、并入与上传，live/、epg/ 文件原样不动。本轮换用点播关键词（tvbox、drpy、影视源、猫影视、cms-api、影视仓、vod-source、影视接口）搜 GitHub，41 个新仓库；其中资源类：songlees355-wq/okay（单仓接口 laosj.json）、youhunwl/TVBox（单仓 tvbox.json + 多仓指针 all.json）、gitoscc/maintv（多仓指针 x.json）、sjnhnp/movie（聚合影视采集资源，未取到 README）、jmfyw/video-api-json（影视 API，未取到 README）；其余多为播放器/引擎/工具（drpy3、drpy-node、CatFun、aimimang 等）未收。网页搜索另发现 LibreTV 点播源合集（haojun19980728-prog/libretv-source-list，39 条）与 aiai86 实测的 14 个 CMS 接口：

- 新增点播源 42 条：CMS 接口 15 条（红牛/量子/金鹰 m3u8 直出、光速 m3u8 直出、U酷、艾旦影视、360、最大、鸭鸭、快车、闪电、樱花、非凡备用、金鹰等，均逐个探活返回真 CMS JSON）、配置内站点 27 条（laosj.json 25 条：量子、西瓜、非凡、大众、巨量、茅台、电影天堂、爱奇艺、新浪、天涯、豆瓣等；tvbox.json 2 条：溢彩秒播、盘他三盘）。现存 867 条。另有 60 条已有点播源补记了新出现的配置文件名。
- 新增 TVBox 配置 4 个：laosj.json（songlees355-wq/okay）、tvbox.json 与 all.json（youhunwl/TVBox）、x.json（gitoscc/maintv）。现存 94 个。半糖仙人.json（gitee 不可达）、tv.xn--yhqu5zs87a.top（520）、0725.json（9xi4o.tk 不可达）、wykj.php（456）探活不通过未收；ymshaoer 实测是 PNG 图片不是配置，未收；yinghezhinan 另外 4 个地址已在库中。
- 跳过：重复 93 条；成人 46 条（OuonnkiTV raw.json 尾部成人段 30 条：麻豆、155、玉兔、番号、老色逼、小鸡、黄色仓库、大奶子、jkun、乐播、森林、辣椒、鲨鱼、豆豆、滴滴、黑料、CK、杏吧、美少女、黄AVZY、白嫖、色猫等；laosj.json 内 🔞站点 16 条）一律未收；不可达 2 条（豆瓣 caiji.dbzy5.com、飘零 p2100.net 远端无响应）；非 CMS 内容 3 条（卧龙、旺旺两个地址返回 HTML 落地页）。OuonnkiTV full-noadult.json 与 ljfbin2 sources.json/echotv.json 与 04:06 版逐字节相同，未重新提取；06:06 轮找到的直播新增（频道 2323、播放列表 7、EPG 2）按 07:02 指令仍不上传。

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
