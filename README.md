# tv-resources

电视直播、点播源、TVBox 配置和追剧资源的整理合集。数据来自下面三个仓库的公开内容，经过去重和清理后按分类存放。整理时间：2026-11-15。

## 文件一览

| 文件 | 内容 | 条数 |
|---|---|---|
| live/live-channels.json | 直播频道（电视 + 电台，正常内容，已去重） | 9942 |
| live/live-channels-invalid.json | 标记为失效的频道，留着复查，不用于播放 | 303 |
| live/live-lines.json | 直播线路（TVBox 配置里的 lives 项，带 EPG/台标模板） | 38 |
| vod/vod-sources.json | TVBox 点播源（sites，去重后） | 798 |
| configs/config-files.json | TVBox 配置文件地址（raw + 镜像）与 spider 引擎 | 13 个配置，8 个 spider |
| epg/epg-sources.json | EPG 模板、EPG id、EPG 播放列表地址 | 3 个模板，1853 个 id，101 个列表 |
| guides/zhuiju-resources.json | 追剧资源（分类、评分、风险、验证记录） | 127 |

## 怎么用

- **TVBox / 影视仓**：在软件里填 `configs/config-files.json` 中任一配置的 `raw_url`（或 `mirror_url`），即可加载整份配置。配置里已经包含点播源和直播线路。
- **直播列表**：`live/live-channels.json` 是一条地址一条频道的清单，每条带频道名、地址、分组、国家、台标、`tvg-id` 和来源。`sources` 字段说明这条地址都出现在哪几个原始文件里，`names` 列出见过的所有频道名。
- **点播源**：`vod/vod-sources.json` 是 TVBox 配置里的 `sites` 项，每条带 `key`、`name`、`type`（0=CMS、1=XPath、3=爬虫）、`api`、`ext` 和搜索/筛选标志，`configs` 说明它出自哪几份配置。
- **节目单**：`epg/epg-sources.json` 里有 EPG 地址模板（`{name}`、`{date}` 占位符）、频道用的 `tvg-id` 清单和 101 个 EPG 播放列表地址。播放列表头写 `x-tvg-url`，频道按 `tvg-id` 匹配节目单。
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
