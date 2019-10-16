---
title: 设置本地连接和WIFI的优先级（同时使用）
top: 2
copyright: true
date: 2019-09-05 15:11:33
categories:
- 实现
- 工具代码
- 计算机网络
tags:
- Windows
- 不走代理同时访问内网和外网
- GMCC
---

**需求**

大概是这么个事儿：

用公司代理上外网时发现过滤了QQ音乐这些听歌网站，顿时不爽(* ￣︿￣)。想着既然本机同时连着本地连接（内网）和热点，凭啥连歌都听不了？于是我就开始了。

<!--more-->

**解决思路**

通过配置系统路由表来实现：

1. 访问内网ip的走本地连接。
2. 访问公网ip的走热点。

通俗来说就是：指定电脑的路由表（地铁线路）数据怎么走（回家坐七号线，去喝酒做六号线），思路借鉴自[论坛帖子](<http://www.xcar.com.cn/bbs/viewthread.php?tid=91536003&page=3> "IE使用有线网络，CHROME使用无线网络 ..")

**大致步骤**  *具体参数视情况修改*  

1. 启动管理员模式的cmd
2. route print 找出你内网连接的网关 *A* 和外网网关 *B*
3. route delete 0.0.0.0 mask 0.0.0.0 *A*
4. route delete 0.0.0.0 mask 0.0.0.0 *B*
5. route -p add 0.0.0.0 mask 0.0.0.0 *B* metric 1
6. route -p add *内网网络号* mask *内网网络掩码* *A* metric 1

然后基本就OK了。

贴张设置完后的路由表吧，重点看永久路由那几项。

 {% asset_img 01.png %}