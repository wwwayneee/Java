# HttpComponents
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/1_httpcomponents.png)</div>

## 前言
---

由于先前的课程中并没有讲过关于网络与信息方面的知识，笔者之也并没有接触过。而这次的选题是HttpComponents，涉及到大量的网络方面的知识，所以在准备这篇报告的第一阶段笔者的主要精力是放在研究一些基本的网络方面的知识。要讲到HttpComponents，就先要讲一下关于http的各种知识。  
##### 第一阶段  
第一阶段解读的重点放在了连接http周边知识上。  
##### 第二阶段
##### 第三阶段

注意！本文档目前还未更新完，完整文档请参考 https://app.gitbook.com/@wwwayneee/s/objectorientedprogramming/

## 相关介绍
介绍一些相关的网络知识  

---

###### http
从万维网（World Wide Web ）服务器传输超文本到本地浏览器，基于请求与响应，无状态的，应用层的协议。
从本地角度去看http协议，就相当于浏览器访问一个url，然后就得到相应的web页面
从服务器角度去看http协议，就相当于客户端（浏览器）链接远程http服务器，服务器返回数据，浏览器接收、解析数据之后显示出来。
###### https
利用SSL（此处：基于应用层的访问控制）进行传输层加密的http传输协议，更加安全。 
代理服务器：代理个人网络从互联网服务商那里获取信息（通过在二者间建立非直接的连接），可以保证安全。
###### 代理服务器
两个网络终端（客户端和服务器）之间的中间代理机构，代理个人网络从服务器那里获取信息。客户端与代理服务器连接之后根据代理使用的协议发送请求（请求与目标服务器进行连接）其中的协议常见的就有http和Socks。
###### Cookies
网站保存在用户端的含有用户信息以及行为的文本，用以弥补http协议的无状态性。举两个例子：  

	1.网站上的记住密码。网站将用户的身份和密码经过加密cookies存在用户硬盘中，下次登录的时候就不用手动输密码了。
	2.上下文相关网址。如果上一个页面会对下一个页面产生影响，那次是就必须使用cookies。比如一个购物网站，上一个页面选好商品，接下来的页面进行支付，支付页面就必须知道上一个页面中购买了什么东西，此时就需要cookies。

客户端发送一个请求到服务器的请求消息格式：（后面还会说到） 请求头部的最后会有一个空行，表示请求头部结束，接下来为请求数据。  

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/2_request_format.png)消息请求格式</div>  

URI(Uniform Resource Identifier，统一资源标识符): web上每一种可用的资源。  
URL(Uniform Resource Locator，统一资源定位符)：一种资源位置的抽象唯一识别方法。  
URL组成：<协议>://<主机>:<端口>/<路径> （端口和路径可以省略，端口默认80）  


<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/3_url.png)URL组成</div>  
http协议的九种请求方法（HttpComponents实现了）  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/4_9ways_of_http_request.png)http协议的九种请求方法</div>  

其中最常用的两种方法：get 和 post  
GET - 从指定的资源请求数据。  
POST - 向指定的资源提交要被处理的数据。  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/5_get_post.png)GET 和 POST</div>  

本文要介绍的HttpComponents：用于提供/对于http服务器的访问功能。

## 关于HttpComponents  
---
HttpComponents：用于提供对于http服务器的访问功能的超文本传输协议，其对HTTP底层协议进行了很好的封装 。  
在构建HTTP客户端或者服务器端应用中很常见，比如WEB浏览器、爬虫、HTTP代理、WEB服务库、基于调整或扩展HTTP协议的分布式通信系统 etc.  

##### 主要功能
实现http方法：GET, HEAD, POST, PUT, DELETE, CONNECT, OPTIONS, TRACE, PATCH 
对https协议的支持（https = http + SSL） 
对代理服务器的支持 
对cookies的支持 
支持在特定的执行上下文（HTTP上下文）中执行HTTP消息——http不行（ 无状态、面向响应请求 ）

##### 组建结构
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/6_httpcomponents_structure.png)HttpComponents 组件结构</div>  

本次分析HttpComponents Core  

## HttpComponents Core  
简称HttpCore  
实现基本http协议的组件，用于搭建客户端和服务器端的http服务。  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/7_guide_book.png)官方文档</div>  

官方文档： httpcore-tutorial http://hc.apache.org/httpcomponents-core-ga/tutorial/pdf/httpcore-tutorial.pdf  

### HttpCore的范围  

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/8_range.png)HttpCore的范围</div>  
### HttpCore的目标  

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/9_target.png)HttpCore的目标</div>  

### HttpCore中所有的包（17个）
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/10_packages.png)HttpCore中所有的包</div>  
### HttpCore中所有的类（252个）
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/11_classes.png)</div>  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/12_classes.png)</div>  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/13_classes.png)</div>  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/14_classes.png)HttpCore中所有的类</div>  

## 重点介绍两个类  

BasicHttpRequest & BasicHttpResponse  
---
### BasicHttpRequest
路径：org.apache.http.message  
继承： AbstractHttpMessage  
实现接口： HttpRequest  

#### BasicHttpRequest中所有方法及其来源  
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/15_BasicHttpRequest.png)BasicHttpRequest中所有方法及其来源</div>  

	Constructors
	构造器：一个类里用于建立对象的方法，与类名相同，没有返回类型，不会被继承，且不会有范围修饰符。
	Java允许构造器重载（一个类被允许拥有多个接受不同参数种类的构造器同时存在，方法名称相同，参数列表不同）
	如果一个类中没有构造方法，那么编译器会为类加上一个默认的构造方法。
	构造器在创建对象的时候调用，为正在创建的对象的成员变量赋初值。
  
    
	
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/16_default_constructor.png)BasicHttpRequest中所有方法及其来源</div>  

#### BasicHttpRequest中构造器  

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/17_Request_constructors.png)BasicHttpRequest中构造器</div>  

接下来分别介绍BasicHttpRequest中的构造器  

```
/**
 * Creates request message with the given method and request path.
 *
 * @param method request method.
 * @param path request path.
 */
public BasicHttpRequest(final String method, final String path) {
    super();
    this.method = method;
    if (path != null) {
        try {
            setUri(new URI(path));
        } catch (final URISyntaxException ex) {
            this.path = path;
        }
    }
}
```
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/18_Request_table_1_4.png)</div>  

```
/**
 * Creates request message with the given method, host and request path.
 *
 * @param method request method.
 * @param host request host.
 * @param path request path.
 *
 * @since 5.0
 */
public BasicHttpRequest(final String method, final HttpHost host, final String path) {
    super();
    this.method = Args.notNull(method, "Method name");
    this.scheme = host != null ? host.getSchemeName() : null;
    this.authority = host != null ? new URIAuthority(host) : null;
    this.path = path;
}
```

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/19_Request_table_2_5.png)</div>  

```
/**
 * Creates request message with the given method, request URI.
 *
 * @param method request method.
 * @param requestUri request URI.
 *
 * @since 5.0
 */
public BasicHttpRequest(final String method, final URI requestUri) {
    super();
    this.method = Args.notNull(method, "Method name");
    setUri(Args.notNull(requestUri, "Request URI"));
}
```

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/20_Request_table_3_6.png)</div>  

```
/**
 * Creates request message with the given method and request path.
 *
 * @param method request method.
 * @param path request path.
 *
 * @since 5.0
 */
public BasicHttpRequest(final Methods method, final String path) {
    super();
    this.method = Args.notNull(method, "Method").name();
    if (path != null) {
        try {
            setUri(new URI(path));
        } catch (final URISyntaxException ex) {
            this.path = path;
        }
    }
}
```
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/18_Request_table_1_4.png)</div>  

```
/**
 * Creates request message with the given method, host and request path.
 *
 * @param method request method.
 * @param host request host.
 * @param path request path.
 *
 * @since 5.0
 */
public BasicHttpRequest(final Methods method, final HttpHost host, final String path) {
    super();
    this.method = Args.notNull(method, "Method").name();
    this.scheme = host != null ? host.getSchemeName() : null;
    this.authority = host != null ? new URIAuthority(host) : null;
    this.path = path;
}
```

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/19_Request_table_2_5.png)</div>  

```
/**
 * Creates request message with the given method, request URI.
 *
 * @param method request method.
 * @param requestUri request URI.
 *
 * @since 5.0
 */
public BasicHttpRequest(final Methods method, final URI requestUri) {
    super();
    this.method = Args.notNull(method, "Method").name();
    setUri(Args.notNull(requestUri, "Request URI"));
}
```


<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/20_Request_table_3_6.png)</div>  

### BasicHttpResponse

路径：org.apache.http.message  
继承： AbstractHttpMessage  
实现接口： HttpResponse  

#### BasicHttpResponse中所有方法及其来源
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/21_BasicHttpResponse.png)BasicHttpResponse中所有方法及其来源</div>  

#### BasicHttpResponse中构造器
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/22_Response_constructors.png)BasicHttpResponse中构造器</div>  

```
/**
 * Creates a new response.
 *
 * @param code              the status code
 * @param catalog           the reason phrase catalog, or
 *                          {@code null} to disable automatic
 *                          reason phrase lookup
 * @param locale            the locale for looking up reason phrases, or
 *                          {@code null} for the system locale
 */
public BasicHttpResponse(
        final int code,
        final ReasonPhraseCatalog catalog,
        final Locale locale) {
    super();
    this.code = Args.positive(code, "Status code");
    this.reasonCatalog = catalog != null ? catalog : EnglishReasonPhraseCatalog.INSTANCE;
    this.locale = locale;
}
```

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/23_Response_table_1.png)</div>  

其中有一个新的概念：status code，状态码，这里介绍一下。  

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/24_status_code.png)status code</div>  

```
/**
 * Creates a new response.
 *
 * @param code          the status code of the response
 * @param reasonPhrase  the reason phrase to the status code, or {@code null}
 */
public BasicHttpResponse(final int code, final String reasonPhrase) {
    this.code = Args.positive(code, "Status code");
    this.reasonPhrase = reasonPhrase;
    this.reasonCatalog = EnglishReasonPhraseCatalog.INSTANCE;
}
```
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/25_Response_table_2.png)</div>  

```
/**
 * Creates a new response.
 *
 * @param code          the status code of the response
 */
public BasicHttpResponse(final int code) {
    this.code = Args.positive(code, "Status code");
    this.reasonPhrase = null;
    this.reasonCatalog = EnglishReasonPhraseCatalog.INSTANCE;
}
```
<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/26_Response_table_3.png)</div>  


## 功能讲解  
### Http请求处理  
---

- 建立连接 
- 接收请求 
- 处理请求 
- 访问资源
- 构建响应 
- 发送响应

<div align="center">![just test](https://raw.githubusercontent.com/wwwayneee/Java/master/Report/pics/26_Response_table_3.png)</div>  

