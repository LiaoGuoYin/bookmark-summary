# [Chrome 扩展] 直接在浏览器中下载 DockerHub 镜像（找不到好的镜像代理的新选择） - V2EX
- URL: https://www.v2ex.com/t/1110052
- Added At: 2025-06-27 05:43:35
- [Link To Text](2025-06-27-[chrome-扩展]-直接在浏览器中下载-dockerhub-镜像（找不到好的镜像代理的新选择）---v2ex_raw.md)

## TL;DR
本文介绍一款Chrome扩展工具"Docker Image Downloader"，能解决Docker镜像下载难题。用户输入镜像名并下载为.tar文件，再通过docker load导入，利用浏览器网络绕过不稳定代理。虽受用户欢迎且便捷，但下载大型镜像时可能出现401错误等稳定性问题，适用于网络受限环境，建议优化开源或Firefox版本。

## Summary
该文章介绍一款解决Docker Hub镜像下载困难的Chrome浏览器扩展工具。核心信息如下：

---

### **开发背景**
- **问题**：`docker pull`常因网络问题卡顿，现有解决方案不稳定（如代理配置、Docker Hub镜像代理服务等）。
- **解决思路**：绕过直接使用Docker CLI，通过浏览器下载镜像文件再导入。

### **工具功能**
- **扩展名称**：Docker Image Downloader
- **操作流程**：  
  1. 在扩展界面输入镜像名称（支持DockerHub、ghcr.io等源）；  
  2. 下载镜像为`.tar`文件；  
  3. 通过 `docker load` 命令导入本地。
- **优势**：利用浏览器网络环境规避常规下载障碍，无需配置Docker守护进程代理。

### **技术原理**
- 通过 **Docker Registry HTTP API** 模拟`docker pull`行为；
- 使用 **[tar-stream](https://github.com/mafintosh/tar-stream)** 流式打包镜像层；
- 依赖 **Chrome扩展V3** 的Service Worker处理Fetch事件，实现流式下载。

### **用户反馈**
1. **积极评价**：  
   - 多用户表示"正需要此工具"并致谢（@leafxen, @OutOfMemery, @ccbikai等）；  
   - 成功下载案例（作者@jujyjse演示输入格式：`kasmweb/core-debian-bookworm:1.14.0`）。
2. **问题反馈**：  
   - 大型镜像下载时报错`401 Unauthorized`（疑因Token过期，耗时约6分钟后中断）；  
   - 需手动设置浏览器全局代理（非扩展内置功能）。
3. **需求建议**：  
   - 呼吁开源或推出Firefox版本（@SunsetShimmer）。

### **补充信息**
- **下载地址**：[Chrome应用商店链接](https://chromewebstore.google.com/detail/docker-image-downloader/dfpojffmnkiglpjpjodlpmoejdcfobnd)  
- **替代方案**：用户提到部分镜像站（如`docker.1panel.live`），但作者认为稳定性不足。

--- 
该工具为容器镜像下载提供了新思路，适用于网络受限环境，但大型镜像稳定性待优化。
