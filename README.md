# 网络代理软件客户端高级技巧

博客：https://ccava.cc

服务购买：https://smusicc.com

客户端下载：http://smusic.ys168.com

# WIN7/10客户端

SSR-WIN：https://github.com/shadowsocksr/shadowsocksr-csharp/releases
SS：https://github.com/shadowsocks

### 用户自定义规则

改用 【用户自定义】 代理规则（系统代理模式选择全局，浏览器扩展也设置 127.0.0.1 1080(默认端口)）

实际上 SSR 安卓客户端中的 ACL 和 代理规则 – 用户自定义 是一样的。

#### 文件位置：

* 代理规则 – 用户自定义 的规则文件是 ShadowsocksR.exe 客户端文件同目录下的 user.rule 文件（如果没有自己新建）。

下方地址中的内容，复制进去就好了：

SSR C# GFWList user.rule ：https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/gfwlist-user.rule

注意：每次修改规则文件后，都需要 重启SSR客户端 才能应用最新规则。

# IOS客户端

### 精简版

用于Surge/Shadowrcket_URL导入方式，阉割了节点定制以及功能开关，其他部分大致相同

Surge：https://raw.githubusercontent.com/lhie1/Surge/master/Surge.conf

Shadowrocket：https://raw.githubusercontent.com/lhie1/Surge/master/Shadowrocket.conf

导入后请务必安装证书

### MitM证书安装

简介：MitM（即 Man-in-the-middle attack，用于解密 HTTPS 的流量）

1. 安装：
* Surge：配置 - 编辑配置 - HTTPS 解密 - 安装证书
* Shadowrocket：设置 - 证书 - 安装证书

2. 信任：
设置 - 通用 - 关于本机 - 证书信任设置 - 信任

# 安卓客户端
SSR-安卓：https://github.com/shadowsocksr/shadowsocksr-android/releases

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

可在高级设置中添加那些网站想通过代理，那些直连

直接复制进去即可，重启软件，即可

#### 添加自定义规则

<pre>
! Put user rules line by line in this file.
! See https://adblockplus.org/en/filter-cheatsheet
||dmm.jp^
||smusic.cc^
||gfw.press^
||adobe.com^
||pornhub.com^
||eroshare.com^
||behance.net^
||pinterest.com^
||500px.com^
||ssrcc.cc^
||ccava.cc^
||smusic.life^
||smusicc.com^

！通配符支持
 *.example.com/*
 *.pornhub.com/*
 *.github.io/*
 *.500px.com/*
 *.smusic.life/*
 *.ccava.cc/*
 *.smusicc.com/*

！满足@@后规则的地址不使用代理
@@*.example.com/*
@@*.qq.com/*
@@*.weixin.com/*
@@*.baidu.com/*
@@*.youku.com/*
</pre>

## 参考
https://github.com/ACL4SSR/ACL4SSR

https://github.com/lhie1/Surge#mitm



