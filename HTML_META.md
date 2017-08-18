# HTML META 元数据标签详解
> 简介：本文分为两部分 理论和实战，讲述META元素中的属性（name、http-equiv）有多少种，分别代表什么意思，以及使用场景

#### 理论知识（理解META）：
***

\<meta\>标签必须位于\<head\> \<\/head\>元素中。

> 参考如下链接   
> [阮一峰老师的元数据（MetaData）](http://www.ruanyifeng.com/blog/2007/03/metadata.html)  
> [MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)  
> [htmldoctor](http://htmldoctor.info/reference/html5/meta.html)
#### 实战开发(怎么用，用那些)：

##### http-equiv
    
```html
<!--服务器允许的方法-->
<!-- Define methods allowed by server (GET, POST etc)  -->
<meta http-equiv="Allow" content="get" />
```
```html
<!--指定返回的数据编码   通常是压缩型  对于g压缩文档，请使用<meta http-equiv =" content-encoding "content ="gzip"-->
<!--  Define the the encoding type of the returned data  -->
<meta http-equiv="Content-Encoding" content="zip" />
```
```html
设定字符集
<!-- 设定网页字符集 html5的方式 -->
<meta charset="utf-8"> 
<!--已过时，推荐使用<meta>元素上的charset。 理解： Define the MIME type for the content 表示发送到浏览器的数据类型，使浏览器知道如何处理接收的数据 or 设定页面使用的字符集 meta标签的charset的信息参数如UTF-8时，代表世界通用的语言编码；-->
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```
```html
<!--已过时，推荐使用 <html> 元素上全局的 lang 属性来替代它. 理解： 这个指令定义页面使用的默认语言. -->
    <meta http-equiv="Content-Language"content="zh-cn"/>
```
```html
<!-- Define the document creation date 包括页面创建的日期和时间。 -->
<meta http-equiv="Date" content="aDate" />
<!-- Define the date when a document was last modified 此内容类型用于页面上次修改的时间和日期设置 -->
<meta http-equiv="Last-Modified" content="aDate" />
```
```html
缓存设定----禁止浏览器缓存
<!-- Define the date when a document is to be reloaded  用于设定网页的到期时间，过期后网页必须到服务器上重新传输。注意：aDate必须使用GMT的时间格式或者设置为0禁用缓存。aDate表示文档设置为过期的日期和时间。 当达到日期时，即使文档存储在缓存中，文档将被重新加载。 这个<meta>元素用于禁用文档的缓存：只需放置一个在日期中传递的日期，这将导致浏览器获取新文件。 如果您希望缓存页面，请将日期设置大点。 请注意，即使将其设置为缓存，IE6将在打开新的浏览器窗口时仍获取用户主页的内容。 -->
    <meta http-equiv="Expires" content="aDate" />
<!-- 当我们在本地测试网页的时候，没有及时更新新内容，可能就是有浏览器缓存。这个时候，我们只要通过使用Meta标签禁用浏览器缓存，可以解决。通用代码如下： -->
<meta http-equiv="expires" content="0" />
<!-- 这样设定，访问者将无法脱机浏览。 -->
<meta http-equiv="pragma" content="no-cache" />
<!-- Cache-Control指定请求和响应遵循的缓存机制。
Cache-Control指定请求和响应遵循的缓存机制。在请求消息或响应消息中设置Cache-Control并不会修改另一个消息处理过程中的缓存处理过程。请求时的缓存指令包括no-cache、no-store、max-age、max-stale、min-fresh、on
ly-if-cached，响应消息中的指令包括public、private、no-cache、no-store、no-transform、must-revalidate、proxy-revalidate、max-age。各个消息中的指令含义如下

Public指示响应可被任何缓存区缓存

Private指示对于单个用户的整个或部分响应消息，不能被共享缓存处理。这允许服务器仅仅描述当用户的部分响应消息，此响应消息对于其他用户的请求无效

no-cache指示请求或响应消息不能缓存

no-store用于防止重要的信息被无意的发布。在请求消息中发送将使得请求和响应消息都不使用缓存。

max-age指示客户机可以接收生存期不大于指定时间（以秒为单位）的响应

min-fresh指示客户机可以接收响应时间小于当前时间加上指定时间的响应

max-stale指示客户机可以接收超出超时期间的响应消息。如果指定max-stale消息的值，那么客户机可以接收超出超时期指定值之内的响应消息。 -->
<meta http-equiv="cache-control" content="no-cache" />
<meta http-equiv ="cache-control"content ="max-age = 0"/> 
<meta http-equiv ="cache-control"content ="no-store"/>
```
```html
 <!-- Define a pages refresh rate (avoid this!)  n是刷新页面的时间间隔：在我们的示例中，页面将每n秒刷新一次。如果包含url，则url2是页面将重定向到的位置-->
    <meta http-equiv="Refresh" content="n;url=url2" />
```
```html
<!-- 此内容类型用于防止页面出现在另一个框架页面中。 -->
<meta http-equiv="window-target" content="_top" />
```
```html
<!-- content-security-policy
允许页面作者定义当前页面的内容策略。内容策略主要指定允许的服务器地址和脚本端点，这有助于防止cross-site scripting 攻击。

CSP 的实质就是白名单制度，开发者明确告诉客户端，哪些外部资源可以加载和执行，等同于提供白名单。它的实现和执行全部由浏览器完成，开发者只需提供配置。

CSP 大大增强了网页的安全性。攻击者即使发现了漏洞，也没法注入脚本，除非还控制了一台列入了白名单的可信主机。
两种方法可以启用 CSP。一种是通过 HTTP 头信息的Content-Security-Policy的字段。 -->
<meta http-equiv="Content-Security-Policy" content="script-src 'self'; object-src 'none'; style-src cdn.example.org third-party.org; child-src https:">
详细参阅：http://www.ruanyifeng.com/blog/2016/09/csp.html
```
```html
<!-- //指定IE和Chrome使用最新版本渲染当前页面 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/> 
```
##### name
> name 特性指定了meta 元素的类型; 说明该元素包含了什么类型的信息。  
> content 指定了实际的元数据内容。

```html
定义正运行在该网页上的网络应用名称；
<meta name="application-name" content="anmin">
```
```html
<!-- 这两个meta 元素对于定义你的页面的作者和提供页面的内容描述是很有用的  -->
<meta name="author" content="Chris Mills">
<!-- 用于标明网页是什么软件做的。 -->
<meta name="generator" content="">
<!-- 用于告诉搜索引擎，你网页的关键字 -->
<meta name="keywords" content="">

<!-- 指定包含关于页面内容的关键字和页面内容的描述是很有用的，因为它可能或让你的页面在搜索引擎的相关的搜索出现得更多 (这些行为术语上被称为 Search Engine Optimization, or SEO ..   包括一个关于页面内容的缩略而精准的描述。一些浏览器，如Firefox和Opera，会使用这个当做网页书签的默认描述。 -->
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">

```
```html
 
<!-- 如果页面不是经常更新，为了减轻搜索引擎爬虫对服务器带来的压力，可以设置一个爬虫的重访时间。如果重访时间过短，爬虫将按它们定义的默认时间来访问。举例： -->

<meta name="revisit-after" content="7 days" >
```
```html
<!-- renderer是为双核浏览器准备的，用于指定双核浏览器默认以何种方式渲染页面。比如说360浏览器。举例： -->
 <!-- //默认webkit内核 -->
<meta name="renderer" content="webkit">
<!-- //默认IE兼容模式 -->
<meta name="renderer" content="ie-comp"> 
 <!-- //默认IE标准模式 -->
<meta name="renderer" content="ie-stand">
```
```html
<!-- 来告诉爬虫哪些页面需要索引，哪些页面不需要索引。 -->
 <meta name="robots">
 <meta name="robots" content="all"> 
 index	允许robot索引本页面（默认）
 noindex	不允许robot索引本页面
 follow	允许搜索引擎继续通过此网页的链接索引搜索其它的网页（默认）
 nofollow	搜索引擎不继续通过此网页的链接索引搜索其它的网页
 none	相当于noindex，nofollow
 noodp	禁止使用Open Directory Project描述（如果有的话）作为搜索引擎结果中的页面描述。
 noarchive	要求搜索引擎不缓存页面内容
 nosnippet	禁止在搜索引擎结果中显示该页面的任何描述。
 noimageindex	要求此页面不作为引用页面的索引图像的显示。
 nocache	和noarchive同义
```
```html
<!-- 
提供了关于viewport初始大小的大小的提示。仅供移动设备使用。
width:整数或device-width  定义viewport的像素宽度，或允许viewport适应设备的屏幕宽度。
height:整数或device-height
initial-scale, 0.0-10.0 定义设备宽度（纵向模式下的设备宽度或横向模式下的设备高度）与viewport大小之间的比例
 minimum-scale, 定义最小的缩放级别。它必须小于或等于maximum-scale，否则视为未定义。浏览器设置可以忽略此规则，iOS10 +默认情况下忽略它。
 maximum-scale定义最大的缩放级别。它必须大于或等于minimum-scale，否则视为未定义。浏览器设置可以忽略此规则，iOS10 +默认情况下忽略它。
 user-scalable	yes 或 no	如果设置为no，用户将无法放大网页。默认值为yes。浏览器设置可以忽略此规则，iOS10 +默认情况下忽略它。
 -->
<meta name="viewport" content="width=500, height=600">
<!-- 禁止缩放： -->
<meta name=”viewport” content=”initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no”/>
```
```html
<!-- 禁止百度转码 -->
<meta http-equiv="Cache-Control" content="no-siteapp"/>
```
```html
<!-- 在移动开发当中，屏蔽数字当作电话号码的代码： -->
<meta name="format-detection" content="telephone=no" />
```
```html
<meta name="copyright" content="Copyright" />
// 定义页面内容版权信息
<meta name="revised" content="web app V.1.0.0" />
// 页面的最新版本
```
```html
由于Chrome M31，您可以设置您的网络应用程序，将应用程序快捷方式图标添加到设备的主屏幕，并使用Chrome for Android的“添加到主屏幕”菜单项，以全屏“应用程序模式”启动该应用程序。
有关mobile-web-app-capable元标记的详细信息，请向下滚动到“在M39之前支持主屏幕安装的应用程序”：

自M31以来，Chrome将在网页的元素中寻找以下元标记（如果有指定显示的清单，则会被忽略）：

<meta name="mobile-web-app-capable" content="yes">

name属性必须是“mobile-web-app-capable”，而content属性必须是“yes”（case in-sensitive）。如果content属性中有任何其他值，则Web应用将作为常规书签添加。
```
```html
Apple 的一些 meta 、 link 效果
[参见APPLE] (https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html#//apple_ref/doc/uid/TP40002051-CH3-SW2)
```
```html
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">
<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- uc强制横屏 -->
<meta name="screen-orientation" content="landscape">
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">
<!-- QQ强制横屏 -->
<meta name="x5-orientation" content="landscape">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">
<!-- 添加智能 App 广告条 Smart App Banner（iOS 6+ Safari） -->
<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">
    
```
```html
针对微软的IE or edge 浏览器的一些站点元数据设置 
https://msdn.microsoft.com/zh-cn/library/gg491732(v=vs.85).aspx
 <meta name="msapplication-TileColor" content="#000"/>
    <!-- Windows 8 磁贴颜色 -->
    <meta name="msapplication-TileImage" content="icon.png"/>
    <!-- Windows 8 磁贴图标 -->
```
  
    
    