Title: [Chrome 扩展] 直接在浏览器中下载 DockerHub 镜像（找不到好的镜像代理的新选择） - V2EX

URL Source: https://www.v2ex.com/t/1110052

Published Time: 2025-02-09T01:53:23Z

Markdown Content:
[Chrome 扩展] 直接在浏览器中下载 DockerHub 镜像（找不到好的镜像代理的新选择） - V2EX

===============

[](https://www.v2ex.com/ "way to explore")

[首页](https://www.v2ex.com/)[注册](https://www.v2ex.com/signup)[登录](https://www.v2ex.com/signin)

**V2EX = way to explore**V2EX 是一个关于分享和探索的地方

[现在注册](https://www.v2ex.com/signup) 已注册用户请 [登录](https://www.v2ex.com/signin)

 爱意满满的作品展示区。 

[广告](https://www.v2ex.com/advertise)

[![Image 3: jujyjse](https://cdn.v2ex.com/avatar/3fe0/a977/176628_large.png?m=1499215124)](https://www.v2ex.com/member/jujyjse)

[V2EX](https://www.v2ex.com/)›[分享创造](https://www.v2ex.com/go/create)
[Chrome 扩展] 直接在浏览器中下载 DockerHub 镜像（找不到好的镜像代理的新选择）
=================================================

[](javascript:)[](javascript:)

[jujyjse](https://www.v2ex.com/member/jujyjse) · 138 天前 · 2204 次点击

这是一个创建于 138 天前的主题，其中的信息可能已经有所发展或是发生改变。

在一些网络环境下，`docker pull` 必会卡的死死的。于是大家想了很多办法：

*   给 docker daemon 挂代理服务器
*   找一个靠谱的 DockerHub 代理（好想现在也没什么太稳定的了）
*   通过大慈善家 Cloudflare 自建一个 DockerHub 代理

这里我做了一个 Chrome 扩展 ，给大家提供了一个新的思路：

**通过浏览器代理直接下载容器镜像文件 tar 文件**，然后使用 `docker load` 导入镜像。

![Image 4: 下载界面](https://lh3.googleusercontent.com/s-1EZrXUB4D4KyvyP-uGn7re2WyA4Ij4ntc33KiesrW-pLJwrVQshkEU_go-nrqjYVWI_MipoDroCjjnvknyiEBt5Q=s1280-w1280-h800)

在扩展弹出的窗口里面直接输入镜像名称即可，除了 DockerHub 外， **[ghcr.io](http://ghcr.io/) 等也都是支持的！**

![Image 5: 下载界面](https://lh3.googleusercontent.com/K_D6mWLAR0UGy9iCcFKjQQ7Wbh04izdui-xvLrqvUUEUaCN6ZYSyXxRhpwYnps0Y2J_IN-oq8M_CqlqEEIOKeb4JVYc=s1280-w1280-h800)

Chrome 商店地址： [https://chromewebstore.google.com/detail/docker-image-downloader/dfpojffmnkiglpjpjodlpmoejdcfobnd](https://chromewebstore.google.com/detail/docker-image-downloader/dfpojffmnkiglpjpjodlpmoejdcfobnd)

* * *

下载器的原理是这样的：

*   根据 Docker Registry HTTP API 来模拟 docker pull 的行为
*   将下载下来的 layers 根据 docker load 支持的格式组装起来，配合 [tar-stream](https://github.com/mafintosh/tar-stream/blob/master/pack.js) 直接流式打包
*   chrome extension v3 支持 service-worker ，service-worker 支持 Fetch Event 可以让用户在浏览器的下载器中直接下载上一步流式打包的 tar 文件

[Chrome 扩展](https://www.v2ex.com/tag/Chrome%20%E6%89%A9%E5%B1%95)[dockerhub](https://www.v2ex.com/tag/dockerhub)[浏览器代理](https://www.v2ex.com/tag/%E6%B5%8F%E8%A7%88%E5%99%A8%E4%BB%A3%E7%90%86)

18 条回复 **•**2025-02-10 19:16:59 +08:00

![Image 6: yyzcl](https://cdn.v2ex.com/avatar/75d3/cfdd/426931_normal.png?m=1718243417)1

**[yyzcl](https://www.v2ex.com/member/yyzcl)**138 天前 via Android

🫡

![Image 7: leafxen](https://cdn.v2ex.com/avatar/b928/5ab4/46305_normal.png?m=1380785686)2

**[leafxen](https://www.v2ex.com/member/leafxen)**138 天前

好用正需要

![Image 8: OutOfMemery](https://cdn.v2ex.com/gravatar/4f4ae939d025324d17ec37b3c0e97a7a?s=48&d=retro)3

**[OutOfMemery](https://www.v2ex.com/member/OutOfMemery)**138 天前

感谢大佬~

![Image 9: ragnaroks](https://cdn.v2ex.com/avatar/6c5f/8507/73740_normal.png?m=1693834882)4

**[ragnaroks](https://www.v2ex.com/member/ragnaroks)**138 天前

[![Image 10](https://i.imgur.com/xVLzpTl.png)](https://i.imgur.com/xVLzpTl.png)

![Image 11: jujyjse](https://cdn.v2ex.com/avatar/3fe0/a977/176628_normal.png?m=1499215124)5

**[jujyjse](https://www.v2ex.com/member/jujyjse)**

OP

138 天前

@[ragnaroks](https://www.v2ex.com/member/ragnaroks) kasmweb/core-debian-bookworm:1.14.0 

DockerHub 的不带前缀就可以了～

![Image 12: SunsetShimmer](https://cdn.v2ex.com/avatar/ebc6/c684/549373_normal.png?m=1743645787)6

**[SunsetShimmer](https://www.v2ex.com/member/SunsetShimmer)**138 天前

期待源码，或者 Firefox 版本。

![Image 13: civetcat](https://cdn.v2ex.com/avatar/5a3d/7727/162162_normal.png?m=1480144468)7

**[civetcat](https://www.v2ex.com/member/civetcat)**138 天前

太有用了，感谢 [![Image 14](https://i.imgur.com/pmNOo2w.png)](https://i.imgur.com/pmNOo2w.png)

![Image 15: AlexRoot](https://cdn.v2ex.com/gravatar/2f2718c8b830e3932af236d8f7d2c9c7?s=48&d=retro)8

**[AlexRoot](https://www.v2ex.com/member/AlexRoot)**138 天前

支持！！！

![Image 16: ccbikai](https://cdn.v2ex.com/avatar/fdbd/ddfe/31662_normal.png?m=1681814708)9

**[ccbikai](https://www.v2ex.com/member/ccbikai)**137 天前![Image 17: ❤️](https://www.v2ex.com/static/img/heart_neue_red.png?v=16ec2dd0a880be6edda1e4a2e35754b3) 3

{

 "registry-mirrors": [

 "[https://docker.1panel.live](https://docker.1panel.live/)",

 "[https://docker.1ms.run](https://docker.1ms.run/)",

 "[https://docker.m.daocloud.io](https://docker.m.daocloud.io/)",

 "[https://registry.dockermirror.com](https://registry.dockermirror.com/)",

 "[https://docker.imgdb.de](https://docker.imgdb.de/)",

 "[https://hub.fast360.xyz](https://hub.fast360.xyz/)"

 ]

}

![Image 18: dkl1999](https://cdn.v2ex.com/gravatar/06e15cb6233ada087c980f6f33fb496f?s=48&d=retro)10

**[dkl1999](https://www.v2ex.com/member/dkl1999)**137 天前

棒

![Image 19: huaji](https://cdn.v2ex.com/gravatar/2458d8b87e8685af6c7d0059cf77dccb?s=48&d=retro)11

**[huaji](https://www.v2ex.com/member/huaji)**137 天前

好好好👍

![Image 20: wm5d8b](https://cdn.v2ex.com/avatar/a799/b6e0/76175_normal.png?m=1486722009)12

**[wm5d8b](https://www.v2ex.com/member/wm5d8b)**137 天前 via Android

@[ccbikai](https://www.v2ex.com/member/ccbikai) daocloud 早就不能用了吧？早年我还用过他们家的面板管理服务器上的容器

![Image 21: macaodoll](https://cdn.v2ex.com/gravatar/00305826ca0b60144a020c9775b6d1f6?s=48&d=retro)13

**[macaodoll](https://www.v2ex.com/member/macaodoll)**137 天前

有趣有用,哈哈哈哈

![Image 22: tankeco](https://cdn.v2ex.com/avatar/8a2a/4864/156877_normal.png?m=1486448723)14

**[tankeco](https://www.v2ex.com/member/tankeco)**137 天前

牛的！ 能支持代理吗？我直连 [hub.docker.com](http://hub.docker.com/) 也不行，挂着 ZeroOmega 才能访问，不太了解浏览器插件能读到我正在使用的代理吗？

![Image 23: tankeco](https://cdn.v2ex.com/avatar/8a2a/4864/156877_normal.png?m=1486448723)15

**[tankeco](https://www.v2ex.com/member/tankeco)**137 天前

哦哦，我把代理设置成全局就可以下载了，感谢大佬！

![Image 24: tankeco](https://cdn.v2ex.com/avatar/8a2a/4864/156877_normal.png?m=1486448723)16

**[tankeco](https://www.v2ex.com/member/tankeco)**137 天前

镜像大了好像有点问题，下一会被取消，401 错误。比如我尝试下这个: qwenllm/qwenvl:2.5-cu121, Request failed with status code 401 Unauthorized: GET [https://registry-1.docker.io/v2/qwenllm/qwenvl/blobs/sha256:fd355de1d1f25492195368f3c3859f24af856e5d7a2ffb34951776daa50bd3e7](https://registry-1.docker.io/v2/qwenllm/qwenvl/blobs/sha256:fd355de1d1f25492195368f3c3859f24af856e5d7a2ffb34951776daa50bd3e7)

![Image 25: jujyjse](https://cdn.v2ex.com/avatar/3fe0/a977/176628_normal.png?m=1499215124)17

**[jujyjse](https://www.v2ex.com/member/jujyjse)**

OP

136 天前

@[tankeco](https://www.v2ex.com/member/tankeco) 大概下了多久遇到了这个问题呢，我怀疑是我在第一步生成的 token 在下载到这个 layer 的时候过期啦？

![Image 26: tankeco](https://cdn.v2ex.com/avatar/8a2a/4864/156877_normal.png?m=1486448723)18

**[tankeco](https://www.v2ex.com/member/tankeco)**136 天前

@[jujyjse](https://www.v2ex.com/member/jujyjse) 6 分钟多点

[](https://www.digitalocean.com/?refcode=1b51f1a7651d)

**[关于](https://www.v2ex.com/about)·[帮助文档](https://www.v2ex.com/help)·[博客](https://blog.v2ex.com/)·[API](https://www.v2ex.com/help/api)·[FAQ](https://www.v2ex.com/faq)·[实用小工具](https://www.v2ex.com/tools)· 5090 人在线**最高记录 6679·[![Image 27](https://www.v2ex.com/static/img/language.png?v=6a5cfa731dc71a3769f6daace6784739) Select Language](https://www.v2ex.com/select/language) 创意工作者们的社区  World is powered by solitude VERSION: 3.9.8.5 · 21ms · [UTC 05:44](https://www.v2ex.com/worldclock#utc) · [PVG 13:44](https://www.v2ex.com/worldclock#pvg) · [LAX 22:44](https://www.v2ex.com/worldclock#lax) · [JFK 01:44](https://www.v2ex.com/worldclock#jfk)

Developed with [CodeLauncher](https://cl.v2ex.pro/)

♥ Do have faith in what you're doing.

❯
