# 网络代理软件客户端-高级技巧

博客：https://ccava.cc

服务购买：https://smusic.life

客户端下载：http://smusic.ys168.com

### 规则可达到的效果

屏蔽广告/国内外自动分流/自定义网站规则（直连OR代理）/拦截运营商劫持/保护隐私

# 常见问题

- 上千行的代理规则，会对上网速度产生影响吗？
> 不会的。我之前也认为这是一个每次网络数据包经过都会执行一次的规则文件，逐行匹配规则，所以需要尽可能精简。但后来和 SR 作者交流后发现这是一个误区，SR 在每次加载规则时都会生成一棵搜索树，可以理解为对主机名从后往前的有限状态机 DFA，并不是逐行匹配，并且对每次的匹配结果还有个哈希缓存。
换句话说，2000 行的规则和 50 行的规则在 SR 中均为同一量级的时间复杂度 O(1)。

- 你提供了这么多规则，如何选择适合我的？
> 黑白名单区别在于对待 境外冷门网站 的不同，黑名单默认直连，而白名单则默认使用代理。前者可能会有被墙的情况出现。后者不会出现无法翻墙的情况，但也许会使用代理去连接原本可以直连的网站，速度变慢，当然，如果你的翻墙服务器速度不低于直连，就果断使用白名单吧。
如果你选择恐惧症爆发，那就两个都下载好了，黑白名单在手，天下无忧。

- 广告过滤不完全？
> 该规则并不保证 100% 过滤所有的广告，尤其是视频广告，与网页广告不同的是，优酷等 App 每次升级都有可能更换一次广告策略，因此难以保证其广告屏蔽的实时有效性。

# WIN7/10客户端

SSR-WIN：https://github.com/smusicsanshu/smusic/blob/master/ssr-win..7z
### PAC模式自定义规则

在用户使用`PAC模式`的前提下，可在菜单`PAC` 下选择 `编辑GFWlist规则`

参考[MAC编辑方法](https://github.com/smusicsanshu/smusic/blob/master/README.md#macos客户端)

### 用户自定义规则

改用 `用户自定义` 代理规则（系统代理模式选择全局，浏览器扩展也设置 127.0.0.1 1080(默认端口)）

实际上 SSR 安卓客户端中的 ACL 和 代理规则 – 用户自定义 是一样的。

### 文件位置：

`代理规则` – `用户自定义` 的规则文件是 ShadowsocksR.exe 

客户端文件同目录下的 `user.rule` 文件（如果没有自己新建）。

下方地址中的内容，复制进去就好了：

SSR GFWList user.rule ：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/gfwlist-user.rule

注意：每次修改规则文件后，都需要 重启SSR客户端 才能应用最新规则。

# IOS客户端

提供多款 Shadowrocket 规则，带广告过滤功能。用于 iOS 未越狱设备选择性地自动翻墙。

### 精简版

用于Surge/Shadowrcket_URL导入方式，阉割了节点定制以及功能开关，其他部分大致相同

Surge：https://raw.githubusercontent.com/lhie1/Surge/master/Surge.conf

Shadowrocket：https://raw.githubusercontent.com/lhie1/Surge/master/Shadowrocket.conf

-------

### 使用方法

打开软件 - 配置 - 点击右上角“+” - 输入上面的地址 - 点击下载 - 选择

### 黑名单过滤 + 广告
黑名单中包含了境外网站中无法访问的那些，对不确定的网站则默认直连。

- 代理：top500 网站中不可直连的境外网站
- 直连：默认直连境外其余网站、中国网站
- 包含广告过滤

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_top500_banlist_ad.conf



### 白名单过滤 + 广告
白名单中包含了境外网站中可以访问的那些，对不确定的网站则默认代理。

- 直连：top500 网站中可直连的境外网站、中国网站
- 代理：默认代理其余的所有境外网站
- 包含广告过滤

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_top500_whitelist_ad.conf



### 黑名单过滤
现在很多浏览器都自带了广告过滤功能，而广告过滤的规则其实较为臃肿，如果你不需要全局地过滤 App 内置广告和视频广告，可以选择这个不带广告过滤的版本。

- 代理：top500 网站中不可直连的境外网站
- 直连：默认直连境外其余网站、中国网站
- 不包含广告过滤

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_top500_banlist.conf



### 白名单过滤
现在很多浏览器都自带了广告过滤功能，而广告过滤的规则其实较为臃肿，如果你不需要全局地过滤 App 内置广告和视频广告，可以选择这个不带广告过滤的版本。

- 直连：top500 网站中可直连的境外网站、中国网站
- 代理：默认代理其余的所有境外网站
- 不包含广告过滤

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_top500_whitelist.conf



### 国内外划分 + 广告
- 国内外划分，对中国网站直连，外国网站代理。包含广告过滤。
- 国外网站总是走代理，对于某些港澳台网站，速度反而会比直连更快。

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_cnip_ad.conf

### 国内外划分
- 国内外划分，对中国网站直连，外国网站代理。不包含广告过滤。
- 国外网站总是走代理，对于某些港澳台网站，速度反而会比直连更快。

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_cnip.conf

### 直连去广告
如果你想将 SR 作为 iOS 全局去广告工具，这个规则会对你有所帮助。

- 直连：所有请求
- 包含广告过滤

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_direct_banad.conf

### 代理去广告
如果你想将 SR 作为 iOS 全局去广告 + 全局翻墙工具，这个规则会对你有所帮助。

- 直连：局域网请求
- 代理：其余所有请求
- 包含广告过滤

规则地址：https://raw.githubusercontent.com/h2y/Shadowrocket-ADBlock-Rules/master/sr_proxy_banad.conf

导入后请务必安装证书

### MitM证书安装

简介：MitM（即 Man-in-the-middle attack，用于解密 HTTPS 的流量）

1. 安装：
* Surge：配置 - 编辑配置 - HTTPS 解密 - 安装证书
* Shadowrocket：设置 - 证书 - 安装证书

2. 信任：
设置 - 通用 - 关于本机 - 证书信任设置 - 信任


# 安卓客户端

SSR-安卓：https://github.com/smusicsanshu/smusic/blob/master/5hadow5ocksr-android.apk

### 使用方法

在软件首页 - `路由设置` - `自定义ACL文件` - 把下面地址`复制`进去即可

### 安卓 SS/SSR 去广告ACL规则

* 屏蔽小米手机和魅族flyme rom系统广告
* 国内网站均直接连接
* 屏蔽常用视频网站广告
* 屏蔽常用网站广告、其他流媒体网站广告
* 屏蔽部分应用程序开屏广告
* 屏蔽部分运营商劫持网页弹出的漂浮球广告、流量统计
* 拦截常用应用程序的隐私跟踪、行为分析、数据统计

### SS/SSR ACL Files Download：

ACL更新地址（白名单）：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/banAD.acl

ACL更新地址（黑名单）：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/gfwlist-banAD.acl

ACL更新地址（全局）：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/onlybanAD.acl

ACL更新地址（仅GFWList）：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/fullgfwlist.acl

ACL更新地址（国内代理）：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/backcn-banAD.acl

ACL更新地址（白名单，无去广告）：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/nobanAD.acl

# MacOS客户端

可在高级设置中添加那些网站想通过代理，那些直连`（前提是使用PAC模式）`

### 使用方法

直接复制进去即可，重启软件，即可（此方法WIN通用）

位置：代理设置 - 编辑PAC用户自定规则

客户端：https://github.com/smusicsanshu/smusic/blob/master/ShadowsocksX-NG-R8.dmg

#### 添加自定义规则

<pre>
! Put user rules line by line in this file.
! See https://adblockplus.org/en/filter-cheatsheet
! Homepage: https://smusicc.com/

! //全部走代理
||dmm.jp^
||gfw.press^
||adobe.com^
||pornhub.com^
||eroshare.com^
||behance.net^
||pinterest.com^
||500px.com^
||ccava.cc^
||smusic.life^
||smusicc.com^

! 通配符支持//全部走代理
 *.example.com/*
 *.pornhub.com/*
 *.github.io/*
 *.500px.com/*
 *.smusic.life/*
 *.ccava.cc/*
 *.smusicc.com/*
 *.pinterest.com/*
 *.behance.net/*

! 满足@@后规则的地址//不使用代理
@@*.example.com/*
@@*.qq.com/*
@@*.weixin.com/*
@@*.baidu.com/*
@@*.youku.com/*
</pre>

## 参考
https://github.com/ACL4SSR/ACL4SSR

https://github.com/lhie1/Surge#mitm

https://github.com/smusicsanshu/Shadowrocket-ADBlock-Rules

