# karing-mihomo-config

基于 [KaringX/karing-ruleset](https://github.com/KaringX/karing-ruleset) 全部 171 个规则碎片 + [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) geosite/geoip 整理的 Clash Meta (mihomo) 配置。

已用 mihomo v1.19.32 内核真实启动验证:89 个规则集全部加载(161719 条规则)、全部策略组就位。

## Raw 直链

```
https://raw.githubusercontent.com/TiaraBasori/karing-mihomo-config/main/karing-mihomo.yaml
```

CDN 加速(国内可达):

```
https://fastly.jsdelivr.net/gh/TiaraBasori/karing-mihomo-config@main/karing-mihomo.yaml
```

## 使用

1. 下载后把 `proxy-providers.nodes.url` 的 `PUT-YOUR-SUBSCRIPTION-URL-HERE` 换成你的订阅链接
2. 首次启动无需代理:89 个规则集全部走 jsdelivr CDN,配置内已强制下载域名直连
3. 规则集每日自动更新(interval: 86400)

## 策略组

### 地区分组(url-test 自动选延迟最低,组内 `filter` 正则匹配中英文名/旗帜 emoji,大小写不敏感、带词边界防误匹配)

`🇭🇰 香港` · `🇹🇼 台湾` · `🇯🇵 日本` · `🇸🇬 新加坡` · `🇺🇸 美国` · `🇷🇺 俄罗斯` · 另有韩国/英国/德国/法国等 17 个国家组 + `🌐 其他地区`(排除上述地区)

`🚀 节点选择` = 手动入口(♻️ 自动选择 / 各地区 / 🌐 其他地区)。

每个功能分组内可直接切换:固定出口(如 DIRECT / REJECT)或 🚀 节点选择 / ♻️ 自动选择 / 任意地区组(🇭🇰🇹🇼🇯🇵🇸🇬🇺🇸🇷🇺 / 🌐 其他地区);地区组内部再由 url-test 自动选该地区延迟最低的节点

### 规则分流组(默认动作)

| 组 | 默认 |
|---|---|
| 🛑 广告拦截 | REJECT |
| 🧹 应用净化 | REJECT |
| ☠️ 恶意软件 | REJECT |
| 📲 电报消息 · 💬 OpenAI · 🤖 Google Gemini · 🔎 Google · ▶️ Google Play | 节点选择 |
| 📢 Google FCM | 直连 |
| 🍎 苹果服务 | 全球直连 |
| 🍎 苹果推送 | 节点选择 |
| 🎧 Spotify | 节点选择 |
| 🚫 Spotify Ads | REJECT |
| 📹 油管视频 · 🦋 Facebook · ❌ X · 🎵 TikTok · 📸 Instagram | 节点选择 |
| 🎥 奈飞视频 | 节点选择 |
| 💬 WhatsApp · ✈️ Claude · 🐱 GitHub | 节点选择 |
| Ⓜ️ 微软Bing · Ⓜ️ 微软服务 | 节点选择 |
| Ⓜ️ 微软云盘 | 全球直连 |
| 🎮 游戏平台 | 节点选择 |
| 📺 哔哩哔哩 · 🎶 网易音乐 | 全球直连 |
| 🌏 国外穿墙 | 节点选择 |
| 🐟 漏网之鱼 | 节点选择 |

## 数据来源与说明

- ACL4SSR 上游 Clash `.list`(与 karing sing 分支碎片同源):BanAD/BanEasyList 系列、Spotify/Telegram/OpenAI/Gemini/GoogleFCM/Apple/YouTube/Netflix/TikTok/Instagram/Facebook/Twitter/WhatsApp/Claude/GitHub/Microsoft/Bing/OneDrive/游戏平台/ChinaDomain/ChinaIp 等 57 个碎片
- MetaCubeX geosite/geoip `.mrs`:category-ads-all、spotify@ads、google-play、googlefcm、apple@cn、x、whatsapp、anthropic、bing、onedrive、geolocation-cn/!cn、tld-cn 等 32 个规则集(每日随上游更新)
- ☠️ 恶意软件组:上游 malware/phishing/cryptominers 仅提供 sing-box `.srs` 格式(mihomo 不支持),组已保留可手动加规则;常见恶意广告域已被 广告拦截 + 应用净化 覆盖
- SteamCN/微软云盘等国内 CDN 已直连;BilibiliHMT(港澳台番剧)、IqiyiHMT(海外站)归入 奈飞视频/游戏平台 代理组
- 盗版影视站(NivodTV/Olevod/VikACG/YYeTs/HWTV)与思杰马克丁钓鱼(Marketing)归入 🧹 应用净化

## 数据来源

- [KaringX/karing-ruleset](https://github.com/KaringX/karing-ruleset) — 碎片清单
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) — Clash 格式规则碎片
- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) — geosite/geoip mrs
