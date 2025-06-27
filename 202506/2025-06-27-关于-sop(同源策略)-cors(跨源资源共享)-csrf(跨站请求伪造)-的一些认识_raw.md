Title: 关于 SOP(同源策略) / CORS(跨源资源共享) / CSRF(跨站请求伪造) 的一些认识

URL Source: https://blog.lyc8503.net/post/cors-and-csrf/

Published Time: 2022-01-20T03:54:55.000Z

Markdown Content:
关于 SOP(同源策略) / CORS(跨源资源共享) / CSRF(跨站请求伪造) 的一些认识

===============

[](https://blog.lyc8503.net/post/cors-and-csrf/#)[](https://blog.lyc8503.net/post/cors-and-csrf/#)[](https://blog.lyc8503.net/post/cors-and-csrf/#)
*   [Home](https://blog.lyc8503.net/index.html)
*   [About](https://blog.lyc8503.net/about/)
*   [Writing](https://blog.lyc8503.net/archives/)
*   [Category](https://blog.lyc8503.net/categories/)
*   [Friends](https://blog.lyc8503.net/friends/)
*   [Search](https://blog.lyc8503.net/search/)

*   [](https://blog.lyc8503.net/post/10-all-in-quickconnect/)
*   [](https://blog.lyc8503.net/post/windows-powertoys/)
*   [](https://blog.lyc8503.net/post/cors-and-csrf/#)
*   [](https://blog.lyc8503.net/post/cors-and-csrf/#)

Previous post Next post Back to top Share post

*   [](https://www.facebook.com/sharer.php?u=https://blog.lyc8503.net/post/cors-and-csrf/)
*   [](https://twitter.com/share?url=https://blog.lyc8503.net/post/cors-and-csrf/&text=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://www.linkedin.com/shareArticle?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](https://pinterest.com/pin/create/bookmarklet/?url=https://blog.lyc8503.net/post/cors-and-csrf/&is_video=false&description=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](mailto:?subject=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86&body=Check%20out%20this%20article:%20https://blog.lyc8503.net/post/cors-and-csrf/)
*   [](https://getpocket.com/save?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://reddit.com/submit?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://www.stumbleupon.com/submit?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://digg.com/submit?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](https://www.tumblr.com/share/link?url=https://blog.lyc8503.net/post/cors-and-csrf/&name=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86&description=%3Cp%3E%3Cstrong%3E%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5%3C/strong%3E%E6%98%AF%E6%8C%87%E5%9C%A8%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E6%8E%92%E7%89%88%E5%BC%95%E6%93%8E%22%3EWeb%E6%B5%8F%E8%A7%88%E5%99%A8%3C/a%3E%E4%B8%AD%EF%BC%8C%E5%85%81%E8%AE%B8%E6%9F%90%E4%B8%AA%E7%BD%91%E9%A1%B5%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E8%85%B3%E6%9C%AC%22%3E%E8%84%9A%E6%9C%AC%3C/a%3E%E8%AE%BF%E9%97%AE%E5%8F%A6%E4%B8%80%E4%B8%AA%E7%BD%91%E9%A1%B5%E7%9A%84%E6%95%B0%E6%8D%AE%EF%BC%8C%E4%BD%86%E5%89%8D%E6%8F%90%E6%98%AF%E8%BF%99%E4%B8%A4%E4%B8%AA%E7%BD%91%E9%A1%B5%E5%BF%85%E9%A1%BB%E6%9C%89%E7%9B%B8%E5%90%8C%E7%9A%84%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E6%A0%87%E5%BF%97%E7%AC%A6%22%3EURI%3C/a%3E%E3%80%81%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E4%B8%BB%E6%A9%9F%E5%90%8D%E7%A8%B1%22%3E%E4%B8%BB%E6%9C%BA%E5%90%8D%3C/a%3E%E5%92%8C%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E9%80%9A%E8%A8%8A%E5%9F%A0%22%3E%E7%AB%AF%E5%8F%A3%E5%8F%B7%3C/a%3E%EF%BC%8C%E4%B8%80%E6%97%A6%E4%B8%A4%E4%B8%AA%E7%BD%91%E7%AB%99%E6%BB%A1%E8%B6%B3%E4%B8%8A%E8%BF%B0%E6%9D%A1%E4%BB%B6%EF%BC%8C%E8%BF%99%E4%B8%A4%E4%B8%AA%E7%BD%91%E7%AB%99%E5%B0%B1%E8%A2%AB%E8%AE%A4%E5%AE%9A%E4%B8%BA%E5%85%B7%E6%9C%89%E7%9B%B8%E5%90%8C%E6%9D%A5%E6%BA%90%E3%80%82%E6%AD%A4%E7%AD%96%E7%95%A5%E5%8F%AF%E9%98%B2%E6%AD%A2%E6%9F%90%E4%B8%AA%E7%BD%91%E9%A1%B5%E4%B8%8A%E7%9A%84%E6%81%B6%E6%84%8F%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E8%84%9A%E6%9C%AC%22%3E%E8%84%9A%E6%9C%AC%3C/a%3E%E9%80%9A%E8%BF%87%E8%AF%A5%E9%A1%B5%E9%9D%A2%E7%9A%84%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E6%96%87%E6%A1%A3%E5%AF%B9%E8%B1%A1%E6%A8%A1%E5%9E%8B%22%3E%E6%96%87%E6%A1%A3%E5%AF%B9%E8%B1%A1%E6%A8%A1%E5%9E%8B%3C/a%3E%E8%AE%BF%E9%97%AE%E5%8F%A6%E4%B8%80%E7%BD%91%E9%A1%B5%E4%B8%8A%E7%9A%84%E6%95%8F%E6%84%9F%E6%95%B0%E6%8D%AE%E3%80%82%3C/p%3E%3Cp%3E%3Cstrong%3E%E8%B7%A8%E5%9F%9F%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB%3C/strong%3E%EF%BC%88%E8%8B%B1%E8%AF%AD%EF%BC%9ACross-origin%20resource%20sharing%EF%BC%8C%E7%BC%A9%E5%86%99%EF%BC%9ACORS%EF%BC%89%EF%BC%8C%E7%94%A8%E4%BA%8E%E8%AE%A9%E7%BD%91%E9%A1%B5%E7%9A%84%E5%8F%97%E9%99%90%E8%B5%84%E6%BA%90%E8%83%BD%E5%A4%9F%E8%A2%AB%E5%85%B6%E4%BB%96%E5%9F%9F%E5%90%8D%E7%9A%84%E9%A1%B5%E9%9D%A2%E8%AE%BF%E9%97%AE%E7%9A%84%E4%B8%80%E7%A7%8D%E6%9C%BA%E5%88%B6%E3%80%82%3C/p%3E%3Cp%3E%3Cstrong%3E%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0%3C/strong%3E%EF%BC%88%E8%8B%B1%E8%AF%AD%EF%BC%9ACross-site%20request%20forgery%EF%BC%89%EF%BC%8C%E4%B9%9F%E8%A2%AB%E7%A7%B0%E4%B8%BA%20%3Cstrong%3Eone-click%20attack%3C/strong%3E%20%E6%88%96%E8%80%85%20%3Cstrong%3Esession%20riding%3C/strong%3E%EF%BC%8C%E9%80%9A%E5%B8%B8%E7%BC%A9%E5%86%99%E4%B8%BA%20%3Cstrong%3ECSRF%3C/strong%3E%20%E6%88%96%E8%80%85%20%3Cstrong%3EXSRF%3C/strong%3E%EF%BC%8C%20%E6%98%AF%E4%B8%80%E7%A7%8D%E6%8C%9F%E5%88%B6%E7%94%A8%E6%88%B7%E5%9C%A8%E5%BD%93%E5%89%8D%E5%B7%B2%E7%99%BB%E5%BD%95%E7%9A%84Web%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E4%B8%8A%E6%89%A7%E8%A1%8C%E9%9D%9E%E6%9C%AC%E6%84%8F%E7%9A%84%E6%93%8D%E4%BD%9C%E7%9A%84%E6%94%BB%E5%87%BB%E6%96%B9%E6%B3%95%E3%80%82%3C/p%3E)
*   [](https://news.ycombinator.com/submitlink?u=https://blog.lyc8503.net/post/cors-and-csrf/&t=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)

1.   [1.0x00 SOP & CORS](https://blog.lyc8503.net/post/cors-and-csrf/#0x00-SOP-CORS)
    1.   [1.1.简单请求](https://blog.lyc8503.net/post/cors-and-csrf/#%E7%AE%80%E5%8D%95%E8%AF%B7%E6%B1%82)

2.   [2.0x01 CSRF](https://blog.lyc8503.net/post/cors-and-csrf/#0x01-CSRF)

关于 SOP(同源策略) / CORS(跨源资源共享) / CSRF(跨站请求伪造) 的一些认识
================================================

lyc8503

2022-01-20

[学习日记](https://blog.lyc8503.net/categories/%E5%AD%A6%E4%B9%A0%E6%97%A5%E8%AE%B0/) › [Web](https://blog.lyc8503.net/categories/%E5%AD%A6%E4%B9%A0%E6%97%A5%E8%AE%B0/Web/)

**同源策略**是指在[Web浏览器](https://zh.wikipedia.org/wiki/%E6%8E%92%E7%89%88%E5%BC%95%E6%93%8E)中，允许某个网页[脚本](https://zh.wikipedia.org/wiki/%E8%85%B3%E6%9C%AC)访问另一个网页的数据，但前提是这两个网页必须有相同的[URI](https://zh.wikipedia.org/wiki/%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E6%A0%87%E5%BF%97%E7%AC%A6)、[主机名](https://zh.wikipedia.org/wiki/%E4%B8%BB%E6%A9%9F%E5%90%8D%E7%A8%B1)和[端口号](https://zh.wikipedia.org/wiki/%E9%80%9A%E8%A8%8A%E5%9F%A0)，一旦两个网站满足上述条件，这两个网站就被认定为具有相同来源。此策略可防止某个网页上的恶意[脚本](https://zh.wikipedia.org/wiki/%E8%84%9A%E6%9C%AC)通过该页面的[文档对象模型](https://zh.wikipedia.org/wiki/%E6%96%87%E6%A1%A3%E5%AF%B9%E8%B1%A1%E6%A8%A1%E5%9E%8B)访问另一网页上的敏感数据。

**跨域资源共享**（英语：Cross-origin resource sharing，缩写：CORS），用于让网页的受限资源能够被其他域名的页面访问的一种机制。

**跨站请求伪造**（英语：Cross-site request forgery），也被称为 **one-click attack** 或者 **session riding**，通常缩写为 **CSRF** 或者 **XSRF**， 是一种挟制用户在当前已登录的Web应用程序上执行非本意的操作的攻击方法。

[](https://blog.lyc8503.net/post/cors-and-csrf/#0x00-SOP-CORS "0x00 SOP & CORS")0x00 SOP & CORS
-----------------------------------------------------------------------------------------------

浏览器中有 _源_ 的概念, 如果两个 URL 的 [protocol](https://developer.mozilla.org/zh-CN/docs/Glossary/Protocol)、[port](https://developer.mozilla.org/en-US/docs/Glossary/Port) (如果有指定的话)和 [host](https://developer.mozilla.org/zh-CN/docs/Glossary/Host) 都相同的话, 则这两个 URL 是 _同源_.

浏览器默认会有同源策略, 用于限制一个 origin 下的页面与其他源的资源进行交互, 跨源的请求会受到限制.

CORS 的配置是由**服务器响应**中的`Access-Control-Allow-xxx` 等 Header 决定的, 主要限制了客户端通过 ajax 方式发起的请求.

比如在前后端分离的开发中, 通过地址 `http://localhost:63343/` 访问前端, 前端中的 javascript 包含如下代码访问未配置 CORS 的后端接口(`http://localhost:8080/user/auth`).

1

2

3

4

5

6

7

8

9 const backend_url = "http://localhost:8080"

$.ajaxSetup({contentType: "application/json; charset=utf-8"});

$.post(backend_url + "/user/auth", JSON.stringify({

 "token": token

}), function (data) {

 // Do something

}).fail(function () {

 // Do something

});

Chrome 报错, 请求失败.

`Access to XMLHttpRequest at 'http://localhost:8080/user/auth' from origin 'http://localhost:63343' has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

但也有的请求是被默认放行的, 具体来说只有符合下列规则的 _简单请求_ 才能被 _暂时放行_, **但如果服务器在返回的请求中未指明 `Access-Control-Allow-Origin` 或 允许的 Origin 不包含当前 Origin, 请求的响应将会被 Chrome 拦截, 不能被 javascript 获取, 但此时在服务器端请求已经完成. 如果请求包含了 Cookie 但响应头部中没有 `Access-Control-Allow-Credentials: true`, 请求的响应同样会被浏览器拦截.**

> ### [](https://blog.lyc8503.net/post/cors-and-csrf/#%E7%AE%80%E5%8D%95%E8%AF%B7%E6%B1%82 "简单请求")[简单请求](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CORS#%E7%AE%80%E5%8D%95%E8%AF%B7%E6%B1%82)
> 
> 
> 某些请求不会触发 [CORS 预检请求](https://developer.mozilla.org/zh-CN/docs/Glossary/Preflight_request)。本文称这样的请求为“简单请求”，请注意，该术语并不属于 [Fetch](https://fetch.spec.whatwg.org/) （其中定义了 CORS）规范。若请求 **满足所有下述条件**，则该请求可视为“简单请求”：
> 
> 
> *   使用下列方法之一：
> *   [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET)
> *   [`HEAD`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/HEAD)
> *   [`POST`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/POST)
> *   除了被用户代理自动设置的首部字段（例如 `Connection`，`User-Agent`）和在 Fetch 规范中定义为禁用首部名称的其他首部，允许人为设置的字段为 Fetch 规范定义的 CORS 安全的首部字段集合。该集合为：
> *   [`Accept`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept)
> *   [`Accept-Language`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept-Language)
> *   [`Content-Language`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Language)
> *   [`Content-Type`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type) （需要注意额外的限制）
> *   `Content-Type`的值仅限于下列三者之一：
> *   `text/plain`
> *   `multipart/form-data`
> *   `application/x-www-form-urlencoded`
> *   请求中的任意 [`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest) 对象均没有注册任何事件监听器；[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest) 对象可以使用 [`XMLHttpRequest.upload`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/upload) 属性访问。
> *   请求中没有使用 [`ReadableStream`](https://developer.mozilla.org/zh-CN/docs/Web/API/ReadableStream) 对象。

(可以发现, 其实默认的 POST 表单是可以跨域的.(为了兼容性考虑.))

而非上述简单请求的**复杂请求**, 浏览器会发出一个 _**预检请求**_ 来获取服务器的 CORS 配置.

**如果未配置 CORS 或 CORS 允许的 Origin 中不包含当前 Origin, 浏览器将不会发出请求, 服务器也不能收到实际请求.**

更多详细信息见: [https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CORS](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CORS)

在 SpringBoot 后端开发时, 最简单的方法是在对应的 Controller 类上加上 `@CrossOrigin` 即可允许跨域.

1

2

3

4

5@RestController

@CrossOrigin

public class UserController {

 // ...

}

或者在 nginx 中配置 api 的反向代理到某个 path, 直接同源访问.

[](https://blog.lyc8503.net/post/cors-and-csrf/#0x01-CSRF "0x01 CSRF")0x01 CSRF
-------------------------------------------------------------------------------

CSRF 即利用浏览器**自动传送 Cookie** 的特性进行攻击.

例如用户在 A 网站上登录了自己的账号, 相关信息储存在 Cookie 中.

用户访问恶意的 B 网站, B 网站构造表单内容提交到 A 网站, 由于访问的是 A 的域名, 浏览器自动带上了 A 域名下的 Cookie, 服务器验证 Cookie 通过后完成 B 网站指定的操作, 而用户毫不知情. **(CORS 默认允许跨域 POST 表单.)**

传统的 CSRF 防御方式是要求在请求中包含 CSRF Token. CSRF Token 可以储存在本域的页面或通过 Cookie 获取. 即通过包含本域才能获取的信息来防止 CSRF.

也可以在服务器后端通过检测 Origin 和 Referer 来防止 CSRF.

前后端分离之后就无法直接在前端页面的 HTML 中包含 CSRF Token 了.

还是可以使用双重 Cookie 的方式 (Cookie 中包含 CSRF Token) 防御 CSRF.

但现在前后端分离的情况下大多使用 JSON 交换数据, 如果后端检验了 `Content-Type` 且设置了正确的`Access-Control-Allow-Origin` 即可以抵御 CSRF.**(跨域的 JSON 请求会被 CORS 默认拦截.)** 见: [https://stackoverflow.com/questions/11008469/are-json-web-services-vulnerable-to-csrf-attacks](https://stackoverflow.com/questions/11008469/are-json-web-services-vulnerable-to-csrf-attacks)

更加现代的用户鉴权方法是 **JWT**, 如果通过在请求头部添加 Token 鉴权, 本身就避免了 CSRF, 可以起到和双重 Cookie 同样的保护效果.

而对于仍然使用 Cookie 鉴权的场景, 现在也已经有了 CSRF 的**终极解决方案**: [SameSite cookies](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Set-Cookie/SameSite).

直接从根源上解决了 CSRF 的问题, 即不再在跨域请求中传送 Cookie, 且近期版本的浏览器将 Lax 作为默认值, 已经可以防御 CSRF 攻击了.

本文采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.en) 许可协议发布.

作者: lyc8503, 文章链接: [https://blog.lyc8503.net/post/cors-and-csrf/](https://blog.lyc8503.net/post/cors-and-csrf/)

如果本文给你带来了帮助或让你觉得有趣, 可以考虑[赞助我](https://blog.lyc8503.net/about/#Sponsor)¬_¬

*   [Home](https://blog.lyc8503.net/index.html)
*   [About](https://blog.lyc8503.net/about/)
*   [Writing](https://blog.lyc8503.net/archives/)
*   [Category](https://blog.lyc8503.net/categories/)
*   [Friends](https://blog.lyc8503.net/friends/)
*   [Search](https://blog.lyc8503.net/search/)

1.   [1.0x00 SOP & CORS](https://blog.lyc8503.net/post/cors-and-csrf/#0x00-SOP-CORS)
    1.   [1.1.简单请求](https://blog.lyc8503.net/post/cors-and-csrf/#%E7%AE%80%E5%8D%95%E8%AF%B7%E6%B1%82)

2.   [2.0x01 CSRF](https://blog.lyc8503.net/post/cors-and-csrf/#0x01-CSRF)

*   [](https://www.facebook.com/sharer.php?u=https://blog.lyc8503.net/post/cors-and-csrf/)
*   [](https://twitter.com/share?url=https://blog.lyc8503.net/post/cors-and-csrf/&text=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://www.linkedin.com/shareArticle?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](https://pinterest.com/pin/create/bookmarklet/?url=https://blog.lyc8503.net/post/cors-and-csrf/&is_video=false&description=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](mailto:?subject=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86&body=Check%20out%20this%20article:%20https://blog.lyc8503.net/post/cors-and-csrf/)
*   [](https://getpocket.com/save?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://reddit.com/submit?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://www.stumbleupon.com/submit?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](http://digg.com/submit?url=https://blog.lyc8503.net/post/cors-and-csrf/&title=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)
*   [](https://www.tumblr.com/share/link?url=https://blog.lyc8503.net/post/cors-and-csrf/&name=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86&description=%3Cp%3E%3Cstrong%3E%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5%3C/strong%3E%E6%98%AF%E6%8C%87%E5%9C%A8%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E6%8E%92%E7%89%88%E5%BC%95%E6%93%8E%22%3EWeb%E6%B5%8F%E8%A7%88%E5%99%A8%3C/a%3E%E4%B8%AD%EF%BC%8C%E5%85%81%E8%AE%B8%E6%9F%90%E4%B8%AA%E7%BD%91%E9%A1%B5%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E8%85%B3%E6%9C%AC%22%3E%E8%84%9A%E6%9C%AC%3C/a%3E%E8%AE%BF%E9%97%AE%E5%8F%A6%E4%B8%80%E4%B8%AA%E7%BD%91%E9%A1%B5%E7%9A%84%E6%95%B0%E6%8D%AE%EF%BC%8C%E4%BD%86%E5%89%8D%E6%8F%90%E6%98%AF%E8%BF%99%E4%B8%A4%E4%B8%AA%E7%BD%91%E9%A1%B5%E5%BF%85%E9%A1%BB%E6%9C%89%E7%9B%B8%E5%90%8C%E7%9A%84%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E6%A0%87%E5%BF%97%E7%AC%A6%22%3EURI%3C/a%3E%E3%80%81%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E4%B8%BB%E6%A9%9F%E5%90%8D%E7%A8%B1%22%3E%E4%B8%BB%E6%9C%BA%E5%90%8D%3C/a%3E%E5%92%8C%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E9%80%9A%E8%A8%8A%E5%9F%A0%22%3E%E7%AB%AF%E5%8F%A3%E5%8F%B7%3C/a%3E%EF%BC%8C%E4%B8%80%E6%97%A6%E4%B8%A4%E4%B8%AA%E7%BD%91%E7%AB%99%E6%BB%A1%E8%B6%B3%E4%B8%8A%E8%BF%B0%E6%9D%A1%E4%BB%B6%EF%BC%8C%E8%BF%99%E4%B8%A4%E4%B8%AA%E7%BD%91%E7%AB%99%E5%B0%B1%E8%A2%AB%E8%AE%A4%E5%AE%9A%E4%B8%BA%E5%85%B7%E6%9C%89%E7%9B%B8%E5%90%8C%E6%9D%A5%E6%BA%90%E3%80%82%E6%AD%A4%E7%AD%96%E7%95%A5%E5%8F%AF%E9%98%B2%E6%AD%A2%E6%9F%90%E4%B8%AA%E7%BD%91%E9%A1%B5%E4%B8%8A%E7%9A%84%E6%81%B6%E6%84%8F%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E8%84%9A%E6%9C%AC%22%3E%E8%84%9A%E6%9C%AC%3C/a%3E%E9%80%9A%E8%BF%87%E8%AF%A5%E9%A1%B5%E9%9D%A2%E7%9A%84%3Ca%20href=%22https://zh.wikipedia.org/wiki/%E6%96%87%E6%A1%A3%E5%AF%B9%E8%B1%A1%E6%A8%A1%E5%9E%8B%22%3E%E6%96%87%E6%A1%A3%E5%AF%B9%E8%B1%A1%E6%A8%A1%E5%9E%8B%3C/a%3E%E8%AE%BF%E9%97%AE%E5%8F%A6%E4%B8%80%E7%BD%91%E9%A1%B5%E4%B8%8A%E7%9A%84%E6%95%8F%E6%84%9F%E6%95%B0%E6%8D%AE%E3%80%82%3C/p%3E%3Cp%3E%3Cstrong%3E%E8%B7%A8%E5%9F%9F%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB%3C/strong%3E%EF%BC%88%E8%8B%B1%E8%AF%AD%EF%BC%9ACross-origin%20resource%20sharing%EF%BC%8C%E7%BC%A9%E5%86%99%EF%BC%9ACORS%EF%BC%89%EF%BC%8C%E7%94%A8%E4%BA%8E%E8%AE%A9%E7%BD%91%E9%A1%B5%E7%9A%84%E5%8F%97%E9%99%90%E8%B5%84%E6%BA%90%E8%83%BD%E5%A4%9F%E8%A2%AB%E5%85%B6%E4%BB%96%E5%9F%9F%E5%90%8D%E7%9A%84%E9%A1%B5%E9%9D%A2%E8%AE%BF%E9%97%AE%E7%9A%84%E4%B8%80%E7%A7%8D%E6%9C%BA%E5%88%B6%E3%80%82%3C/p%3E%3Cp%3E%3Cstrong%3E%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0%3C/strong%3E%EF%BC%88%E8%8B%B1%E8%AF%AD%EF%BC%9ACross-site%20request%20forgery%EF%BC%89%EF%BC%8C%E4%B9%9F%E8%A2%AB%E7%A7%B0%E4%B8%BA%20%3Cstrong%3Eone-click%20attack%3C/strong%3E%20%E6%88%96%E8%80%85%20%3Cstrong%3Esession%20riding%3C/strong%3E%EF%BC%8C%E9%80%9A%E5%B8%B8%E7%BC%A9%E5%86%99%E4%B8%BA%20%3Cstrong%3ECSRF%3C/strong%3E%20%E6%88%96%E8%80%85%20%3Cstrong%3EXSRF%3C/strong%3E%EF%BC%8C%20%E6%98%AF%E4%B8%80%E7%A7%8D%E6%8C%9F%E5%88%B6%E7%94%A8%E6%88%B7%E5%9C%A8%E5%BD%93%E5%89%8D%E5%B7%B2%E7%99%BB%E5%BD%95%E7%9A%84Web%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E4%B8%8A%E6%89%A7%E8%A1%8C%E9%9D%9E%E6%9C%AC%E6%84%8F%E7%9A%84%E6%93%8D%E4%BD%9C%E7%9A%84%E6%94%BB%E5%87%BB%E6%96%B9%E6%B3%95%E3%80%82%3C/p%3E)
*   [](https://news.ycombinator.com/submitlink?u=https://blog.lyc8503.net/post/cors-and-csrf/&t=%E5%85%B3%E4%BA%8E%20SOP(%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5)%20/%20CORS(%E8%B7%A8%E6%BA%90%E8%B5%84%E6%BA%90%E5%85%B1%E4%BA%AB)%20/%20CSRF(%E8%B7%A8%E7%AB%99%E8%AF%B7%E6%B1%82%E4%BC%AA%E9%80%A0)%20%E7%9A%84%E4%B8%80%E4%BA%9B%E8%AE%A4%E8%AF%86)

[Menu](https://blog.lyc8503.net/post/cors-and-csrf/#)[TOC](https://blog.lyc8503.net/post/cors-and-csrf/#)[Share](https://blog.lyc8503.net/post/cors-and-csrf/#)[Top](https://blog.lyc8503.net/post/cors-and-csrf/#)

Copyright © 2018-2025 lyc8503

*   [Home](https://blog.lyc8503.net/index.html)
*   [About](https://blog.lyc8503.net/about/)
*   [Writing](https://blog.lyc8503.net/archives/)
*   [Category](https://blog.lyc8503.net/categories/)
*   [Friends](https://blog.lyc8503.net/friends/)
*   [Search](https://blog.lyc8503.net/search/)
