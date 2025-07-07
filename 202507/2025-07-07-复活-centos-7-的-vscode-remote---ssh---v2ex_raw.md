Title: 复活 CentOS 7 的 VSCode Remote - SSH - V2EX

URL Source: https://www.v2ex.com/t/1126786

Published Time: 2025-04-20T04:49:30Z

Markdown Content:
复活 CentOS 7 的 VSCode Remote - SSH - V2EX

===============

[](https://www.v2ex.com/ "way to explore")

[首页](https://www.v2ex.com/)[注册](https://www.v2ex.com/signup)[登录](https://www.v2ex.com/signin)

**V2EX = way to explore**V2EX 是一个关于分享和探索的地方

[现在注册](https://www.v2ex.com/signup) 已注册用户请 [登录](https://www.v2ex.com/signin)

›[Visual Studio Code](https://code.visualstudio.com/)

颜值和功能齐聚的跨平台SSH工具

[![Image 1](https://cid.v2ex.pro/ipfs/QmWiszwB8uDZ1GRnoYj22s6mXLY4H7F1jKage5xQViFwDB)](https://www.xterminal.cn/)

Xterminal 是一款强大的开发工具，不止是 SSH 与 Terminal，还集成了 Note、拥有快捷动作、命令提示等特性

[前往下载](https://www.xterminal.cn/)

Promoted by [Moyyyyyyyyyyye](https://www.v2ex.com/member/Moyyyyyyyyyyye)

[PRO](https://www.v2ex.com/pro/about)

[![Image 2: mikewang](https://cdn.v2ex.com/avatar/b728/8030/81681_large.png?m=1683726911)](https://www.v2ex.com/member/mikewang)

[V2EX](https://www.v2ex.com/)›[Visual Studio Code](https://www.v2ex.com/go/vscode)
复活 CentOS 7 的 VSCode Remote - SSH
=================================

[2](javascript:)[](javascript:)

[mikewang](https://www.v2ex.com/member/mikewang) · [MikeWang000000](https://github.com/MikeWang000000) · 78 天前 · 3113 次点击

这是一个创建于 78 天前的主题，其中的信息可能已经有所发展或是发生改变。

vscode-server-centos7
=====================

GitHub：

[https://github.com/MikeWang000000/vscode-server-centos7](https://github.com/MikeWang000000/vscode-server-centos7)

简介
--

从 VSCode v1.99 版本开始，SSH 插件将无法在 RHEL/CentOS 7 上运行，因为它们的 glibc 、libstdc++ 已不再满足最新版本的最低要求。

使用以下步骤即可复活：

1.   进入 [Releases](https://github.com/MikeWang000000/vscode-server-centos7/releases) 页面，下载对应的版本的压缩包，放到服务器上；

2.   在服务器上登录你的帐户，执行以下命令：

```bash
mkdir -p ~/.vscode-server
tar xzf vscode-server_*.tar.gz -C ~/.vscode-server --strip-components 1
~/.vscode-server/code-latest --patch-now
```
3.   使用 SSH 插件连接服务器，完成。

特点
--

1.   此 repo 使用最新版本的 glibc 、libstdc++ 编译放至 `~/.vscode-server/gnu` 目录下，并修改 VSCode Server 相关 ELF 的 `.interp` 节，做到不升级/修改系统库，仅对 VSCode 相关二进制文件生效。

2.   在 SSH 上远程安装的插件也会被自动链接至最新的 glibc 、libstdc++。

升级 VSCode
---------

如果升级了 VSCode 版本，需要重新到 GitHub 上下载对应的版本，然后手动安装 Server 端，替换掉官方的版本。

补充说明
----

CentOS 7 是一个很旧的 Linux 发行版了，升级到最新版本的操作系统始终是最推荐的。

然而，某些特定的场景下我们仍需使用 CentOS 7 进行开发，例如客户提出的旧版本 Linux 兼容性要求，或者基于 CentOS 7 兼容的信创系统适配等等。

此 repo 目标在于临时解决这类问题，不过我还是希望大家都能快快升级吧。

[VSCode](https://www.v2ex.com/tag/VSCode)[remote-ssh](https://www.v2ex.com/tag/remote-ssh)[centos7](https://www.v2ex.com/tag/centos7)

16 条回复 **•**2025-04-30 19:57:38 +08:00

![Image 3: nagisaushio](https://cdn.v2ex.com/avatar/cc0a/2c9a/661506_normal.png?m=1703076362)1

**[nagisaushio](https://www.v2ex.com/member/nagisaushio)**78 天前 via Android

我之前写了个更方便的，只要提供 glibc 和 patchelf 即可，不用自己魔改

[https://github.com/hsfzxjy/vscode-remote-glibc-patch](https://github.com/hsfzxjy/vscode-remote-glibc-patch)

![Image 4: ysc3839](https://cdn.v2ex.com/avatar/c307/29ad/27712_normal.png?m=1682522765)2

**[ysc3839](https://www.v2ex.com/member/ysc3839)**78 天前

@[nagisaushio](https://www.v2ex.com/member/nagisaushio) 我自己的方案是从 CentOS 8 的源下载新版 glibc 包，从 patchelf GitHub release 下载最新的预编译包，解压到 /opt 下面，然后设置 vscode 的那三个环境变量。

![Image 5: hanxiV2EX](https://cdn.v2ex.com/avatar/2d5f/b1ec/172691_normal.png?m=1748604017)3

**[hanxiV2EX](https://www.v2ex.com/member/hanxiV2EX)**78 天前 via Android![Image 6: ❤️](https://www.v2ex.com/static/img/heart_neue_red.png?v=16ec2dd0a880be6edda1e4a2e35754b3) 1

我的方法是用 docker ，用 docker 启动一个最新的 ubuntu ，里面装好 ssh ，把 dot 目录都挂载进去，什么版本都没问题了。。。

![Image 7: nagisaushio](https://cdn.v2ex.com/avatar/cc0a/2c9a/661506_normal.png?m=1703076362)4

**[nagisaushio](https://www.v2ex.com/member/nagisaushio)**78 天前 via Android

@[ysc3839](https://www.v2ex.com/member/ysc3839) CentOS 8 那个我试过好像报了 kernel too old ，索性自己编译了

![Image 8: mikewang](https://cdn.v2ex.com/avatar/b728/8030/81681_normal.png?m=1683726911)5

**[mikewang](https://www.v2ex.com/member/mikewang)**

OP

78 天前![Image 9: ❤️](https://www.v2ex.com/static/img/heart_neue_red.png?v=16ec2dd0a880be6edda1e4a2e35754b3) 1

@[nagisaushio](https://www.v2ex.com/member/nagisaushio) #1

其实原先我也是直接 patchelf 的，但是插件会有些问题。

比如 C/C++ 这个插件，就算 SSH 插件能正常用了，但它还是没法启动 gdb 调试，因为插件里 OpenDebugAD7 这个二进制也需要最新的 glibc 。[https://github.com/microsoft/vscode-cpptools/issues/13219](https://github.com/microsoft/vscode-cpptools/issues/13219)

所以这个还做了额外的工作，使用 inotify 监控 extensions.json ，检测到安装新插件时，自动给插件打补丁。然后还判断是否为 glibc 的二进制，排除使用 musl 的二进制（有些还是 musl 动态链接的）。

![Image 10: mikewang](https://cdn.v2ex.com/avatar/b728/8030/81681_normal.png?m=1683726911)6

**[mikewang](https://www.v2ex.com/member/mikewang)**

OP

78 天前

@[hanxiV2EX](https://www.v2ex.com/member/hanxiV2EX) #3 因为我写 C 和 C++，还是需要旧 glibc 编译的，所以 docker 这条路就行不通了🤦‍♂️

![Image 11: nagisaushio](https://cdn.v2ex.com/avatar/cc0a/2c9a/661506_normal.png?m=1703076362)7

**[nagisaushio](https://www.v2ex.com/member/nagisaushio)**78 天前 via Android

@[mikewang](https://www.v2ex.com/member/mikewang) #5 可以可以，这个没想到

![Image 12: ysc3839](https://cdn.v2ex.com/avatar/c307/29ad/27712_normal.png?m=1682522765)8

**[ysc3839](https://www.v2ex.com/member/ysc3839)**78 天前

@[nagisaushio](https://www.v2ex.com/member/nagisaushio) 要求 glibc >= 2.28 ，CentOS 8 刚好就是 2.28 。

@[mikewang](https://www.v2ex.com/member/mikewang) 我目前在 CentOS 7 docker 里面开发 C++，似乎没遇到什么错误。

![Image 13: tt0411](https://cdn.v2ex.com/avatar/8611/3dc5/30703_normal.png?m=1736472782)9

**[tt0411](https://www.v2ex.com/member/tt0411)**78 天前

[https://code.visualstudio.com/docs/remote/faq#_can-i-run-vs-code-server-on-older-linux-distributions](https://code.visualstudio.com/docs/remote/faq#_can-i-run-vs-code-server-on-older-linux-distributions) 官方提供的 walkaround 原理基本相同

![Image 14: tt0411](https://cdn.v2ex.com/avatar/8611/3dc5/30703_normal.png?m=1736472782)10

**[tt0411](https://www.v2ex.com/member/tt0411)**78 天前

@[hanxiV2EX](https://www.v2ex.com/member/hanxiV2EX) 暴露 docker 容器里面的 ssh 端口给本机的 vscode 吗?

![Image 15: hanxiV2EX](https://cdn.v2ex.com/avatar/2d5f/b1ec/172691_normal.png?m=1748604017)11

**[hanxiV2EX](https://www.v2ex.com/member/hanxiV2EX)**78 天前

@[tt0411](https://www.v2ex.com/member/tt0411) 是的，比如暴露 2222 端口，然后.ssh 目录和.vscode-server 目录都映射进去，都能复用的。

![Image 16: mikewang](https://cdn.v2ex.com/avatar/b728/8030/81681_normal.png?m=1683726911)12

**[mikewang](https://www.v2ex.com/member/mikewang)**

OP

78 天前

@[tt0411](https://www.v2ex.com/member/tt0411) #9 是的，我这里就是简化了所有步骤：

- 将 patchelf 做成了 libpatchelf 静态编译进去 (libpatchelf/libpatchelf.h)

- 自带编译好的 glibc 和 libstdc++

- 修改了 glibc ，将系统目录改为当前目录，这样改 .interp 就行了，不用再改 rpath 。事实上这么做也更安全。(patches/glibc.patch)

然后加上了额外的功能，就是自动处理插件。官方的方案只能让 server 能用，实测很多 native 插件还是不行的。

做的就是一个开箱即用，不用配参数。

![Image 17: tlanyan](https://cdn.v2ex.com/avatar/da8f/9146/374237_normal.png?m=1745110451)13

**[tlanyan](https://www.v2ex.com/member/tlanyan)**78 天前

印象中从 1.93 版本，server 端就不支持 CentOS 7 了

![Image 18: ysc3839](https://cdn.v2ex.com/avatar/c307/29ad/27712_normal.png?m=1682522765)14

**[ysc3839](https://www.v2ex.com/member/ysc3839)**68 天前 via Android

连接远程机子 Docker 内的 CentOS 7 会报错

[4945 ms] Command failed: /root/.vscode-server/bin/17baf841131aa23349f217ca7c570c76ee87b957/bin/code-server --log debug --force-disable-user-env --server-data-dir /root/.vscode-server --telemetry-level all --accept-server-license-terms --host 127.0.0.1 --port 0 --connection-token-file /root/.vscode-server/data/Machine/.connection-token-17baf841131aa23349f217ca7c570c76ee87b957 --extensions-download-dir /root/.vscode-server/extensionsCache --start-server --skip-requirements-check

[4945 ms] /root/.vscode-server/bin/17baf841131aa23349f217ca7c570c76ee87b957/node: /lib64/libm.so.6: version `GLIBC_2.27' not found (required by /root/.vscode-server/bin/17baf841131aa23349f217ca7c570c76ee87b957/node)

似乎是没修改 node ？能否修复一下？

![Image 19: mikewang](https://cdn.v2ex.com/avatar/b728/8030/81681_normal.png?m=1683726911)15

**[mikewang](https://www.v2ex.com/member/mikewang)**

OP

68 天前

@[ysc3839](https://www.v2ex.com/member/ysc3839) #14

不应该，可以重新执行一下：

~/.vscode-server/code-latest --patch-now

上面会显示被修改的文件。比对一下就知道了。

也可以确认下 VSCode 客户端和服务端的版本号是否匹配：

~/.vscode-server/code-latest --version

不同版本的 server 路径不一样。

![Image 20: ysc3839](https://cdn.v2ex.com/avatar/c307/29ad/27712_normal.png?m=1682522765)16

**[ysc3839](https://www.v2ex.com/member/ysc3839)**67 天前 via Android

@[mikewang](https://www.v2ex.com/member/mikewang) 执行过很多次了，印象中修改的文件没有 node 。客户端版本是 1.99.3 。晚点我重现一下

[](https://www.digitalocean.com/?refcode=1b51f1a7651d)

**[关于](https://www.v2ex.com/about)·[帮助文档](https://www.v2ex.com/help)·[自助推广系统](https://www.v2ex.com/pro/about)·[博客](https://blog.v2ex.com/)·[API](https://www.v2ex.com/help/api)·[FAQ](https://www.v2ex.com/faq)·[实用小工具](https://www.v2ex.com/tools)· 3230 人在线**最高记录 6679·[![Image 21](https://www.v2ex.com/static/img/language.png?v=6a5cfa731dc71a3769f6daace6784739) Select Language](https://www.v2ex.com/select/language) 创意工作者们的社区  World is powered by solitude VERSION: 3.9.8.5 · 29ms · [UTC 11:14](https://www.v2ex.com/worldclock#utc) · [PVG 19:14](https://www.v2ex.com/worldclock#pvg) · [LAX 04:14](https://www.v2ex.com/worldclock#lax) · [JFK 07:14](https://www.v2ex.com/worldclock#jfk)

Developed with [CodeLauncher](https://cl.v2ex.pro/)

♥ Do have faith in what you're doing.

❯
