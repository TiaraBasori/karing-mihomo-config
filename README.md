# karing-clash-meta

基于 [KaringX/karing-ruleset](https://github.com/KaringX/karing-ruleset) 全部规则碎片整理的 Clash Meta (mihomo) 规则配置。

已用 mihomo v1.19.32 内核真实启动验证。

## 文件

| 文件 | 说明 |
|------|------|
| `karing-clash-meta.yaml` | **远程引用版(推荐日常用)** — karing 官方 `recommend/cn.json` 同款编排,49 个 ACL4SSR 核心碎片 + 21 个 MetaCubeX geosite/geoip mrs,规则集每日自动更新 |
| `karing-clash-meta-full-inline.yaml.zst` | **全量内联版(压缩包)** — 仓库全部 171 个碎片收录(去广告 87505 条 / 直连 10146 条 / 代理 8165 条),单文件即用、离线可用,解压后 5.6MB |
| `fragment-classification.md` | 171 个碎片的归类清单(去广告 / 直连 / 代理),方便自行增删 |

## Raw 直链

远程引用版(可直接填进 Clash Meta / mihomo 的「配置下载」):

```
https://raw.githubusercontent.com/TiaraBasori/karing-clash-meta/main/karing-clash-meta.yaml
```

全量内联版(解压后使用;`zstd -d` 解压或用支持 zstd 的解压工具):

```
https://raw.githubusercontent.com/TiaraBasori/karing-clash-meta/main/karing-clash-meta-full-inline.yaml.zst
```

CDN 加速(国内可达,与 raw 内容一致):

```
https://fastly.jsdelivr.net/gh/TiaraBasori/karing-clash-meta@main/karing-clash-meta.yaml
https://fastly.jsdelivr.net/gh/TiaraBasori/karing-clash-meta@main/karing-clash-meta-full-inline.yaml.zst
```

## 使用

1. 下载配置后,把 `proxy-providers.nodes.url` 的 `PUT-YOUR-SUBSCRIPTION-URL-HERE` 换成你的订阅链接
2. 远程引用版首次启动无需代理:71 个规则集全部走 jsdelivr CDN,且配置内已强制这些下载域名直连
3. 策略组:🚀 节点选择 / 🛑 广告拦截 / Ⓜ️ 微软服务 / 🍎 苹果服务 / 📲 电报消息 / 💬 OpenAI / 📹 油管视频 / 🎥 国外媒体 / 🎮 游戏平台 / 🎯 全球直连 / 🐟 漏网之鱼

## 与上游的对应关系

- 仓库 `sing` 分支的 `.srs` 是 sing-box 专用格式,Clash Meta 不支持;本配置的碎片一一对应上游 [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) 的 Clash `.list`(170/171 同名)与 [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) 的 `.mrs`
- karing 独有的 `BanADCompany`(131 条)以内联形式收录
- 源碎片中 9 条 `URL-REGEX` 规则 mihomo 不支持(仅有的不兼容项),对应域名已被 DOMAIN 规则覆盖,已剔除
- 上游 `geoip/openai`、`geoip/github` 已移除(404),OpenAI / GitHub 由域名集覆盖

## 数据来源

- [KaringX/karing-ruleset](https://github.com/KaringX/karing-ruleset) — 碎片清单与官方编排
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) — Clash 格式规则碎片
- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) — geosite/geoip mrs
