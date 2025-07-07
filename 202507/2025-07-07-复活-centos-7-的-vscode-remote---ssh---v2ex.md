# 复活 CentOS 7 的 VSCode Remote - SSH - V2EX
- URL: https://www.v2ex.com/t/1126786
- Added At: 2025-07-07 11:16:21
- [Link To Text](2025-07-07-复活-centos-7-的-vscode-remote---ssh---v2ex_raw.md)

## TL;DR
由于CentOS 7的旧glibc/libstdc++导致VSCode Remote-SSH故障，可临时通过MikeWang的GitHub补丁包解决：下载解压至服务器目录，应用后优先使用本地新库自动修复兼容性问题。建议优先升级操作系统，此为临时过渡方案。（字数：70）

## Summary
由于CentOS 7的glibc和libstdc++版本过低，从VSCode 1.99版本开始无法运行Remote-SSH功能。这里提供一个临时解决方案，来自MikeWang的GitHub仓库（https://github.com/MikeWang000000/vscode-server-centos7）：

### **核心问题**
- CentOS 7的glibc和libstdc++不满足VSCode要求，导致插件无法运行。官方已停止支持旧版本系统。

### **解决方案步骤**
1. **下载补丁包**：从[Releases页面](https://github.com/MikeWang000000/vscode-server-centos7/releases)获取对应VSCode版本的压缩包（如`vscode-server_*.tar.gz`）。
2. **服务器端操作**：
   - 登录服务器，执行命令：
     ```bash
     mkdir -p ~/.vscode-server
     tar xzf vscode-server_*.tar.gz -C ~/.vscode-server --strip-components 1
     ~/.vscode-server/code-latest --patch-now
     ```
3. **连接VSCode**：使用Remote-SSH插件连接服务器即可正常使用。

### **修复原理与特点**
- **原理**：补丁包内置较新的glibc和libstdc++到`~/.vscode-server/gnu`目录，并通过修改二进制文件的`.interp`节使其优先使用新库，避免升级系统。
- **优势**：
  - 自动处理插件兼容性问题（如C/C++插件依赖的OpenDebugAD7），使用inotify监控并实时修复新安装插件的库链接问题。
  - 兼容musl编译的二进制文件，不修改系统库，安全性更高。
- **升级注意**：若更新VSCode客户端版本，需重新下载并应用补丁包。

### **相关讨论点**
- 其他用户提出简化方案：
  - [nagisaushio的工具](https://github.com/hsfzxjy/vscode-remote-glibc-patch)只需手动提供glibc和`patchelf`。
  - [官方Walkaround](https://code.visualstudio.com/docs/remote/faq#_can-i-run-vs-code-server-on-older-linux-distributions)类似但需自行配置环境变量。
- Docker替代方案：在容器内运行新版Ubuntu并映射SSH端口（例如端口`2222`），挂载用户目录复用配置。
- OP强调其工具更全面，能自动修复插件依赖性，是开箱即用的方案。

### **建议**
- 优先升级操作系统（如CentOS 8+或Ubuntu），此方案仅作为旧系统过渡（如客户兼容性或信创系统要求）。CentOS 7已过时，长期不推荐使用。
