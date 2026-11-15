# tv-resources

电视直播、点播源、TVBox 配置和追剧资源的整理合集。数据来自下面三个仓库的公开内容，经过去重和清理后按分类存放。整理时间：2026-11-15。

## 文件一览

| 文件 | 内容 | 条数 |
|---|---|---|
| live/live-channels.json | 直播频道（电视 + 电台，正常内容，已去重） | 9942 |
| live/live-channels-invalid.json | 标记为失效的频道，留着复查，不用于播放 | 303 |
| live/live-lines.json | 直播线路（TVBox 配置里的 lives 项，带 EPG/台标模板）+ 播放列表（全网搜索探活通过的 M3U/TXT 列表地址） | 37 条线路，73 条播放列表 |
| vod/vod-sources.json | TVBox 点播源（sites，去重后） | 797 |
| configs/config-files.json | TVBox 配置文件地址（raw + 镜像）与 spider 引擎、CMS 节点 | 65 个配置，8 个 spider，1 个 CMS 节点 |
| epg/epg-sources.json | EPG 模板、EPG id、EPG 播放列表地址、DIYP 接口、台标模板 | 3 个模板，1853 个 id，127 个列表，1 个 DIYP 接口，1 个台标模板 |
| guides/zhuiju-resources.json | 追剧资源（分类、评分、风险、验证记录） | 127 |

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
- **直播列表**：`live/live-channels.json` 是一条地址一条频道的清单，每条带频道名、地址、分组、国家、台标、`tvg-id` 和来源。`sources` 字段说明这条地址都出现在哪几个原始文件里，`names` 列出见过的所有频道名。`live/live-lines.json` 里新增的 `playlists` 分组是探活通过的 M3U/TXT 播放列表地址（65 条），可直接订阅或导入播放器；`lines` 仍是 TVBox 配置里的 lives 项。
- **点播源**：`vod/vod-sources.json` 是 TVBox 配置里的 `sites` 项，每条带 `key`、`name`、`type`（0=CMS、1=XPath、3=爬虫）、`api`、`ext` 和搜索/筛选标志，`configs` 说明它出自哪几份配置。
- **节目单**：`epg/epg-sources.json` 里有 EPG 地址模板（`{name}`、`{date}` 占位符）、频道用的 `tvg-id` 清单和 121 个 EPG 播放列表地址，另有 1 个 DIYP 接口端点和 1 个台标模板（范明明 `https://live.fanmingming.cn/tv/{name}.png`）。播放列表头写 `x-tvg-url`，频道按 `tvg-id` 匹配节目单。
- **追剧资源**：`guides/zhuiju-resources.json` 每条带分类、五维评分（资源多、速度、干净、稳定、易用）、四维风险（版权、安全、隐私、支付）和验证记录。

## 数据来源

- [ciweihaha/tvbox](https://github.com/ciweihaha/tvbox)（fork 自 qist/tvbox）：TVBox 配置、点播源、直播列表。
- [ciweihaha/awesome-zhuiju-free](https://github.com/ciweihaha/awesome-zhuiju-free)（fork 自 laoma528/awesome-zhuiju-free）：追剧资源清单。
- [ciweihaha/IPTV](https://github.com/ciweihaha/IPTV)（fork 自 Free-TV/IPTV）：各国频道表和总播放列表。

## 整理方法

- **归一化**：地址去首尾空格，协议和域名小写，去掉默认端口（80/443），去掉无意义的尾部斜杠，去掉 fragment；查询参数保留（带 token 的流地址不能丢）。
- **去重**：同一个归一化地址只保留一条，来源记在 `sources` / `configs` 里。去重前 57253 条，去重后 51672 条，合并了直播频道 5100 条、点播源 462 条、直播线路 10 条、追剧资源 1 条。
- **清理**：去掉空地址、格式错误、带空格、缺协议头的地址共 212 条，去掉缺地址或地址无效的直播线路 4 条。127.0.0.1、localhost、10/172.16/192.168 内网地址直接清理（本机地址放进公开列表没有意义）。
- **分类**：直播、点播源、配置地址、追剧资源、EPG 分开存放；失效频道单独放 `live/live-channels-invalid.json` 留着复查；成人内容（分组名“性视界”，来自 listx.m3u / livex.m3u，共 40464 条）只放在本地文件 `live/live-channels-adult.json`，不混进正常列表，也不上传到本仓库。

## 注意

- 这些地址大多是第三方收集来的，稳定性和版权都不如自有源，只适合做补充参考，不适合替换自有链路。
- 直播频道建议先按“3 次探测、6 档状态”的方法探活后再用（失效的不直接删，复查活了再移回来）。
- 本仓库只做整理，不生产流；上游源失效、改版是常态，数据会随时间过期。
