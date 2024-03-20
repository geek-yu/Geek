[General]
# ✰以"#" ";" 和 "//" 开头的行为注释行
# ✰具体配置请参考Surge使用手册 https://manual.nssurge.com
# > HTTP API
http-api = geek@0.0.0.0:6166
# > 跳过代理
skip-proxy = 239.255.255.250/32, 127.0.0.1, 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12, 100.64.0.0/10, 17.0.0.0/8, localhost, *.local, *.crashlytics.com
# > Always Real IP Hosts
always-real-ip = *.srv.nintendo.net, *.stun.playstation.net, xbox.*.microsoft.com, *.xboxlive.com
# > Hijack DNS
hijack-dns = *:53
# > 允许 Wi-Fi 访问macOS
http-listen = 0.0.0.0:8888
socks5-listen = 0.0.0.0:8889
# > 允许 Wi-Fi 访问iOS
allow-wifi-access = false
wifi-access-http-port = 6152
wifi-access-socks5-port = 6153
# > 网络访问延迟测速URL
internet-test-url = http://www.aliyun.com
# > 代理延迟测速URL
proxy-test-url = http://cp.cloudflare.com/generate_204
# 默认向 8.8.8.8 查询 apple.com，可使用 proxy-test-udp 参数修改，如 proxy-test-udp = google.com@1.1.1.1
proxy-test-udp = apple.com@8.8.8.8
# > 测试超时（秒）
test-timeout = 5
# > 排除简单主机名
exclude-simple-hostnames = true
# > IPv6 支持
ipv6 = false
# > 当遇到 REJECT 策略时返回错误页
show-error-page-for-reject = true
# > Wi-Fi 不是主接口则使用SSID组的默认策略
use-default-policy-if-wifi-not-primary = false
# > 增强版 Wi-Fi 助理
wifi-assist = false
# > ---DNS 服务器---
dns-server = 119.29.29.29, 223.5.5.5, 114.114.114.114
encrypted-dns-server = quic://dns.alidns.com:853, quic://223.5.5.5:853
# > 从/etc/hosts读取DNS记录
read-etc-hosts = true
# > 路由防火墙
# 包含所有的网络请求
include-all-networks = false
# 包含本地网络请求
include-local-networks = false
# > 自定义GeoIP数据库
geoip-maxmind-url = https://cdn.jsdelivr.net/gh/Hackl0us/GeoIP2-CN@release/Country.mmdb
# > GeoIP 数据库自动更新
disable-geoip-db-auto-update = false
# > UDP IP 防泄漏
udp-policy-not-supported-behaviour = REJECT
# > HTTP-API-TLS
http-api-tls = false
# > Web 控制器
http-api-web-dashboard = true
# > 隐藏 VPN 图标
hide-vpn-icon = false
# > All Hybrid 网络并发
all-hybrid = false
# > 允许个人热点使用代理
allow-hotspot-access = true
# > 使 Surge 将 TCP 连接视为 HTTP 请求。Surge HTTP 引擎将处理请求，并且所有高级功能都将可用，例如捕获、重写和脚本编写
force-http-engine-hosts = *.ott.cibntv.net,
# > 提高处理 UDP 流量优先级
udp-priority = false
# > 网络优化
compatibility-mode = 1
# > 代理请求本地DNS映射
use-local-host-item-for-proxy = true
# ipv6
ipv6-vif = auto
# 投屏
# tun-excluded-routes = 198.51.100.0/24, 203.0.113.0/24, 224.0.0.0/4, 239.255.255.250/32, 240.0.0.0/4, 255.255.255.255/32

[Proxy]
# > 本地服务器
# Cloudflare
WARP+SG = wireguard, section-name=Cloudflare, underlying-proxy=𝙎𝙂, test-url=http://cp.cloudflare.com/generate_204, ip-version=prefer-v6
WARP+HK = wireguard, section-name=Cloudflare, underlying-proxy=𝙃𝙆, test-url=http://cp.cloudflare.com/generate_204, ip-version=prefer-v6

[Proxy Group]
# > 自定义策略
# 节点订阅
Nodes = select, policy-path=你的组合订阅, update-interval=43200, interval=600, no-alert=0, hidden=0, include-all-proxies=0
# 代理选择
PROXY = select, AUTO, Nodes, WARP+HK, WARP+SG, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, 𝙐𝙎, EU, no-alert=0, hidden=0, include-all-proxies=0, update-interval=0
# 苹果
Apple = select, PROXY, DIRECT, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, KR+, no-alert=0, hidden=0, include-all-proxies=0
# tg
Telegram = select, PROXY, WARP+SG, 𝙃𝙆, 𝙏𝙒, KR+, 𝙅𝙋, 𝙐𝙎, 𝙎𝙂, EU, no-alert=0, hidden=0, include-all-proxies=0, persistent=0
# 迪士尼
𝓓𝓲𝓼𝓷𝓮𝔂+ = select, PROXY, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, KR+, EU, no-alert=0, hidden=0, 
include-all-proxies=0
# 谷歌
Google = select, PROXY, WARP+SG, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, EU, KR+, no-alert=0, hidden=0, include-all-proxies=0
# ig
Instagram = select, PROXY, WARP+SG, 𝙎𝙂, 𝙅𝙋, 𝙏𝙒, 𝙐𝙎, EU, 𝙃𝙆, KR+, no-alert=0, hidden=0, include-all-proxies=0
# 声田
Spotify = select, PROXY, DIRECT, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, EU, 𝙎𝙂, KR+, no-alert=0, hidden=0, include-all-proxies=0
# Tk
TikTok = select, PROXY, 𝙐𝙎, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, EU, KR+, no-alert=0, hidden=0, include-all-proxies=0
# b站
Bilibili = select, PROXY, 𝙃𝙆, 𝙏𝙒, no-alert=0, hidden=0, include-all-proxies=0
# 油管
YouTube = select, PROXY, WARP+HK, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, EU, 𝙎𝙂, KR+, no-alert=0, hidden=0, include-all-proxies=0
# 奈飞
X = select, PROXY, 𝙃𝙆, 𝙐𝙎, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, EU, KR+, no-alert=0, hidden=0, include-all-proxies=0
# 奈飞
Netflix = select, PROXY, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, EU, KR+, no-alert=0, hidden=0, include-all-proxies=0
# 脸书
Facebook = select, PROXY, 𝙅𝙋, 𝙃𝙆, 𝙐𝙎, 𝙏𝙒, 𝙎𝙂, EU, KR+, no-alert=0, hidden=0, include-all-proxies=0
# 游戏直播
Twittch = select, PROXY, 𝙎𝙂, 𝙅𝙋, 𝙏𝙒, 𝙃𝙆, 𝙐𝙎, KR+, EU, no-alert=0, hidden=0, include-all-proxies=0
# 微软
Microsoft = select, PROXY, 𝙃𝙆, 𝙅𝙋, 𝙎𝙂, 𝙏𝙒, 𝙐𝙎, EU, KR+, no-alert=0, hidden=0, include-all-proxies=0
# 速度测试
Speedtest = select, PROXY, DIRECT, 𝙐𝙎, 𝙃𝙆, 𝙏𝙒, 𝙅𝙋, 𝙎𝙂, EU, no-alert=0, hidden=0, include-all-proxies=0
# ai
ChatGPT = select, PROXY, 𝙐𝙎, 𝙅𝙋, EU, no-alert=0, hidden=0, include-all-proxies=0
# 自动选择
AUTO = url-test, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0
# 台湾
𝙏𝙒 = fallback, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=台|台湾|🇼🇸
# 香港
𝙃𝙆 = fallback, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=港|🇭🇰
# 日本
𝙅𝙋 = fallback, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=日|🇯🇵
# 韩国
KR+ = fallback, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=（|🇰🇷|🇫🇷|🇳🇱|🇮🇳|🇹🇷|）
# 新加坡
𝙎𝙂 = fallback, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=(狮城|新|新加坡|🇸🇬|SG)
# 美国
𝙐𝙎 = fallback, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=(美|美国|🇺🇸|US|us)
# 德英
EU = url-test, include-other-group=Nodes, no-alert=0, hidden=1, include-all-proxies=0, policy-regex-filter=（🇩🇪|🇬🇧|🇫🇷|🇳🇱|🇮🇹|🇺🇦|🇮🇳|India）

[Rule]
# > 抖音本地分流
DOMAIN-SUFFIX,snssdk.com,DIRECT
DOMAIN-SUFFIX,amemv.com,DIRECT
# 苹果TestFlight 商店
DOMAIN,beta.apple.com,PROXY
OR,((DOMAIN,iosapps.itunes.apple.com), (DOMAIN,www.apple.com.cn), (DOMAIN,gateway.icloud.com.cn)),DIRECT // 国内苹果域名直连
# > 其它
OR,((DOMAIN,www.voachinese.com), (DOMAIN,gdb.voanews.com), (DOMAIN,av.voanews.com), (DOMAIN,voa-video-hls-ns.akamaized.net), (DOMAIN,voa-ingest.akamaized.net)),WARP+HK // 美国之音代理
OR,((DOMAIN,cdn.smoot.apple.com), (DOMAIN,time.apple.com), (DOMAIN,app-measurement.com)),REJECT // 去苹果与其它垃圾域名
# ---逻辑规则---
AND,((DEST-PORT,443), (PROTOCOL,QUIC)),REJECT // 屏蔽QUIC流量进入指定端口
AND,((DEST-PORT,443), (PROTOCOL,UDP)),REJECT
DOMAIN,voice.google.com,𝙐𝙎 // 谷歌语音
# 后续规则修正
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Direct/Direct.list,DIRECT
# 广告拦截
DOMAIN-SET,https://raw.githubusercontent.com/privacy-protection-tools/anti-AD/master/anti-ad-surge2.txt,REJECT
# WARP分流
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Cloudflare/Cloudflare.list,WARP+SG
RULE-SET,https://raw.githubusercontent.com/EAlyce/conf/main/Rule/Warp.list,WARP+HK
# Ai
RULE-SET,https://raw.githubusercontent.com/EAlyce/conf/main/Rule/OpenAI.list,ChatGPT
# 软件代码库
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/GitHub/GitHub.list,PROXY
# >  ins
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Instagram/Instagram.list,Instagram
# > 电报
RULE-SET,https://github.com/LucaLin233/Luca_Conf/blob/main/Surge/Rule/Telegram.list?raw=true,Telegram
# > 脸书
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Facebook/Facebook.list,Facebook
# >  游戏直播
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Twitch/Twitch.list,Twittch
# Privacy 隐私
# DOMAIN-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Privacy/Privacy_Domain.list,REJECT
# Hijacking 运营商劫持或恶意网站
# DOMAIN-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Hijacking/Hijacking.list,REJECT
# Netflix
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Netflix/Netflix.list,Netflix
# Disney+
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Disney/Disney.list,𝓓𝓲𝓼𝓷𝓮𝔂+
# YouTube
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/YouTube/YouTube.list,YouTube
# Spotify
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Spotify/Spotify.list,Spotify
# TikTok
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/TikTok/TikTok.list,TikTok
# Bilibili
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/BiliBili/BiliBili.list,Bilibili
# Google
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Google/Google.list,Google
# Twitter
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Twitter/Twitter.list,X
# Speedtest
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Speedtest/Speedtest.list,Speedtest
# Apple
RULE-SET,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/Apple/Apple_All_No_Resolve.list,Apple
# Microsoft
RULE-SET,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Microsoft.list,Microsoft
# Surge 的自动 REJECT 保护丢包，防止应用循环请求
IP-CIDR,0.0.0.0/32,REJECT,no-resolve
# Local Area Network 局域网
RULE-SET,LAN,DIRECT
# GeoIP China
GEOIP,CN,DIRECT
# ---Final规则---
FINAL,PROXY,dns-failed

[Host]
# Firebase Cloud Messaging
mtalk.google.com = 108.177.125.188
# Google Dl
dl.google.com = server:119.29.29.29
dl.l.google.com = server:119.29.29.29
update.googleapis.com = server:119.29.29.29
# PlayStation
*.dl.playstation.net = server:119.29.29.29
# > 淘宝
*.taobao.com = server:https://dns.alidns.com/dns-query // 淘宝
# > 天猫
*.tmall.com = server:https://dns.alidns.com/dns-query // 天猫
# > 阿里云
*.alicdn.com = server:223.5.5.5
*.aliyun.com = server:223.5.5.5
# > 腾讯
*.tencent.com = server:119.29.29.29
*.qq.com = server:119.29.29.29
*.qlogo.cn = server:119.29.29.29
*.qpic.cn = server:119.29.29.29
*.weixin.qq.com = server:119.29.29.29
*.wx.qq.com = server:119.29.29.29
*.weixin.com = server:119.29.29.29
*.weixinbridge.com = server:119.29.29.29
*.wechat.com = server:119.29.29.29
*.servicewechat.com = server:119.29.29.29
# > 京东
*.jd.com = server:119.28.28.28
# > 哔哩哔喱
*.bilibili.com = server:119.29.29.29
hdslb.com = server:119.29.29.29
# > 百度
*.baidu.com = server:180.76.76.76
*.bdstatic.com = server:180.76.76.76 // 百度 静态资源
# 𝐀𝐩𝐩𝐥𝐞
*.apple.com = server:https://doh.dns.apple.com/dns-query
*.itunes.com = server:https://doh.dns.apple.com/dns-query
token.safebrowsing.apple = 17.253.85.207
proxy.safebrowsing.apple = 17.253.85.208
# 
# iosapps.itunes.apple.com = 17.253.85.201

[URL Rewrite]
# 有两种重定向方式: 'header' 和 '302'
# 建议用模块
阻止google.com 跳转到google.com.hk header
^https?:\/\/(www\.)?g\.cn https://www.google.com/ncr 302
^https?:\/\/(www\.)?google\.cn https://www.google.com/ncr 302

[Header Rewrite]
^https?:\/\/api(.*)\.smoot\.apple\.(com|cn)\/ header-replace accept-encoding gzip

[MITM]
# 跳过服务端证书验证
tcp-connection = true
h2 = true
hostname = -api-glb-aapne1c.smoot.apple.com, -s.youtube.com, -api2.smoot.apple.com, -m.baidu.com, -www.youtube.com, -yfamily.ml, -github.com, -91porn.com, -www.xiaohongshu.com, -www.baidu.com, -gitlab.com, -raw.githubusercontent.com, sub.store, -mp.weixin.qq.com, security.wechat.com, -weather-data.apple.com, ios-*.prod.ftl.netflix.com, ios.prod.ftl.netflix.com, security.wechat.com, weixin110.qq.com
