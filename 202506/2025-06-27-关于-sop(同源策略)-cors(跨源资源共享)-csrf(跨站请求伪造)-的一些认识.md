# 关于 SOP(同源策略) / CORS(跨源资源共享) / CSRF(跨站请求伪造) 的一些认识
- URL: https://blog.lyc8503.net/post/cors-and-csrf/
- Added At: 2025-06-27 05:05:17
- [Link To Text](2025-06-27-关于-sop(同源策略)-cors(跨源资源共享)-csrf(跨站请求伪造)-的一些认识_raw.md)

## TL;DR
## 文章总结

本文详细介绍了Web安全中的三个核心概念：同源策略(SOP)、跨域资源共享(CORS)和跨站请求伪造(CSRF)。文章解释了CORS的工作机制，包括简单请求和复杂请求的区别，以及预检机制。重点分析了CSRF攻击原理——利用浏览器自动传送Cookie的特性进行恶意操作，并提供了多种防御方法，从传统的Token验证到现代的SameSite Cookies设置。文章强调在前后端分离开发中，正确配置CORS和使用JWT认证的重要性。

## Summary
## 核心概念定义

**同源策略(SOP)**：浏览器安全机制，要求两个URL的协议、主机名和端口号都相同才能互相访问资源，防止恶意脚本访问其他网页的敏感数据

**跨域资源共享(CORS)**：允许网页受限资源被其他域名页面访问的机制，通过服务器响应头`Access-Control-Allow-xxx`进行配置

**跨站请求伪造(CSRF)**：利用浏览器自动传送Cookie特性，挟制用户在已登录的Web应用上执行非本意操作的攻击方法

## CORS工作机制

### 请求分类
- **简单请求**：满足特定条件的请求（GET/HEAD/POST，特定Headers，特定Content-Type）可以暂时放行，但如果服务器响应中缺少正确的CORS配置，浏览器会拦截响应
- **复杂请求**：不满足简单请求条件的请求，浏览器会先发送预检请求获取CORS配置，未正确配置则不发送实际请求

### 关键特性
- CORS配置由服务器响应头决定，主要限制JavaScript AJAX请求
- 默认POST表单可以跨域（兼容性考虑）
- 前后端分离开发中需要配置CORS或使用nginx反向代理

## CSRF攻击原理与防御

### 攻击原理
1. 用户在网站A登录，Cookie中存储认证信息
2. 用户访问恶意网站B
3. 网站B构造表单提交到网站A
4. 浏览器自动带上网站A的Cookie，完成未授权操作

### 防御方法
- **传统方法**：CSRF Token验证、检测Origin和Referer头部
- **双重Cookie**：在Cookie中包含CSRF Token
- **现代方法**：
  - JWT认证（通过请求头部传递Token）
  - JSON数据交换+正确CORS配置（跨域JSON请求被默认拦截）
  - **SameSite Cookies**：从根源解决问题，不在跨域请求中传送Cookie，现代浏览器默认启用

## 实际应用建议

### 前后端分离场景
- 使用JSON数据交换并正确配置CORS可防御CSRF
- SpringBoot中使用`@CrossOrigin`注解简单配置跨域
- 推荐使用JWT Token认证替代Cookie认证

### 安全最佳实践
- 现代浏览器的SameSite=Lax默认设置已能有效防御CSRF攻击
- 结合多种防御手段以提高安全性
- 正确理解CORS不是安全功能，而是放宽同源策略的机制
