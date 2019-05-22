only for me
目录：
- [Web-Security-Learning](#web-security-learning)
- [Web Security](#web-security)
    - [sql注入](#sql%E6%B3%A8%E5%85%A5)
        - [MySql](#mysql)
        - [MSSQL](#mssql)
        - [PostgreSQL](#postgresql)
        - [MongoDB](#mongodb)
    - [XSS](#xss)
    - [CSRF](#csrf)
    - [其他前端安全](#%E5%85%B6%E4%BB%96%E5%89%8D%E7%AB%AF%E5%AE%89%E5%85%A8)
    - [SSRF](#ssrf)
    - [XXE](#xxe)
    - [JSONP注入](#jsonp%E6%B3%A8%E5%85%A5)
    - [SSTI](#ssti)
    - [代码执行 / 命令执行](#%E4%BB%A3%E7%A0%81%E6%89%A7%E8%A1%8C--%E5%91%BD%E4%BB%A4%E6%89%A7%E8%A1%8C)
    - [文件包含](#%E6%96%87%E4%BB%B6%E5%8C%85%E5%90%AB)
    - [文件上传 / 解析漏洞](#%E6%96%87%E4%BB%B6%E4%B8%8A%E4%BC%A0--%E8%A7%A3%E6%9E%90%E6%BC%8F%E6%B4%9E)
    - [逻辑漏洞](#%E9%80%BB%E8%BE%91%E6%BC%8F%E6%B4%9E)
    - [弱口令](#%e5%bc%b1%e5%8f%a3%e4%bb%a4)
    - [其他漏洞](#%E5%85%B6%E4%BB%96%E6%BC%8F%E6%B4%9E)
        - [RPO(relative path overwrite)](#rporelative-path-overwrite)
        - [Web Cache](#web-cache)
        - [redis](#redis)
    - [PHP相关](#php%E7%9B%B8%E5%85%B3)
        - [弱类型](#%E5%BC%B1%E7%B1%BB%E5%9E%8B)
        - [随机数问题](#%E9%9A%8F%E6%9C%BA%E6%95%B0%E9%97%AE%E9%A2%98)
        - [伪协议](#%E4%BC%AA%E5%8D%8F%E8%AE%AE)
        - [序列化](#%E5%BA%8F%E5%88%97%E5%8C%96)
        - [php mail header injection](#php-mail-header-injection)
        - [其他](#%E5%85%B6%E4%BB%96)
    - [java-Web](#java-web)
        - [反序列](#%E5%8F%8D%E5%BA%8F%E5%88%97)
        - [Struct2](#struct2)
        - [其他](#%E5%85%B6%E4%BB%96-1)
    - [python-Web](#python-web)
    - [Node-js](#node-js)
- [渗透测试](#%E6%B8%97%E9%80%8F%E6%B5%8B%E8%AF%95)

<!-- more -->

# Web Security
## sql注入
### MySql
### MSSQL
### PostgreSQL
### MongoDB
## XSS
## CSRF
## 其他前端安全
## SSRF
+ [小米某处SSRF漏洞(可内网SHELL 附多线程Fuzz脚本)](https://shuimugan.com/bug/view?bug_no=215779)下载图片处,利用302跳转绕过限制,使用dict协议+phpinfo()页面中泄漏的内网地址和端口就可以通过页面加载时间探测端口,6379端口getshell
+ [腾讯某处SSRF漏洞(非常好的利用点)附利用脚本](https://shuimugan.com/bug/view?bug_no=215419)分享功能处,可以直接用http协议探测内网,也可以利用302跳转绕过对协议的限制，使用dict协议获得Redis服务器Shell
+ [华为某分站存在SSRF漏洞](https://shuimugan.com/bug/view?bug_no=214331)下载功能处,内网:访问127.0.0.1:22回显ssh、外网:请求vps可以检测到请求，
+ [新浪微博某处SSRF漏洞](https://shuimugan.com/bug/view?bug_no=214334)分享功能处
+ [有道翻译某处SSRF可通网易内网](https://shuimugan.com/bug/view?bug_no=198176)网页翻译处
+ [有道翻译SSRF修复不完整可绕过](https://shuimugan.com/bug/view?bug_no=214261)xip.io,xip.name,短地址均可绕过
+ [百度某处SSRF可漫游内网](https://shuimugan.com/bug/view?bug_no=214138)漏洞在测试网站"移动友好度"处,直接在vps的文件里写入<iframe src="http://10.16.83.164:8080">绕过，
+ [bilibili某分站从信息泄露到ssrf再到命令执行](https://shuimugan.com/bug/view?bug_no=213982)
+ [七牛某站SSRF可探测内网](https://shuimugan.com/bug/view?bug_no=210934)获取远程图片处ssrf+elasticsearch未授权访问泄露内网网段=探测内网
+ [有道翻译某处SSRF可通网易内网](https://shuimugan.com/bug/view?bug_no=198176)网页翻译处
+ [有道翻译某处SSRF可通网易内网](https://shuimugan.com/bug/view?bug_no=198176)网页翻译处

## XXE
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)在线格式化XML工具存在xxe,XXE读取到脚本文件/home/run/ssh_go.sh，内含SSH登陆密码。
+ [百度某平台Blind XXE漏洞&可Bool型SSRF攻击](https://shuimugan.com/bug/view?bug_no=134057)XML检查工具存在xxe
+ [搜狗某平台Blind XXE漏洞(读取文件/SSRF/Struts2命令执行)](https://shuimugan.com/bug/view?bug_no=135397)XML检查工具存在xxe
+ [百度某功能XML实体注入](https://shuimugan.com/bug/view?bug_no=58381)该功能点将用户输入的svg转换为对应的JPG图片，抓包构造特殊的svg文件然后下载图片，在图片中有回显
+ [百度某功能XML实体注入（二）](https://shuimugan.com/bug/view?bug_no=59783)在第一次修复后只过滤了ENTITY这个词，DTD 本身就支持调用外部的DTD文件，因此我们只需要在svg里加一个外部的DTD就绕过了
+ [鲜果网RSS导入Blind XXE漏洞](https://shuimugan.com/bug/view?bug_no=74069)支持导入OPML文件格式的订阅
+ [博客园某处XXE可下载任意文件](https://shuimugan.com/bug/view?bug_no=111828)博客搬家功能，可以通过导入XML添加博客
+ [用友人力资源管理软件全版本XXE漏洞](https://shuimugan.com/bug/view?bug_no=117316)登陆与重置密码时使用XML传输数据。
+ [AOL Website XML External Entity(XXE) Vulnerability](https://shuimugan.com/bug/view?bug_no=148793)xmlrpc
+ [国际php框架slim架构上存在XXE漏洞](https://shuimugan.com/bug/view?bug_no=156208)根据content-type来区分解析数据。新版本需求php5.5以上，以为不存在xxe，事实上xml外部实体的解析，和php版本并无关系，而是和编译时的libxml库版本有关
+ [唯品会存在Blind XXE 漏洞](https://shuimugan.com/bug/view?bug_no=168457) xfire是流行的webservice开发组件，其在invoke时使用了STAX解析XML导致XML实体注入发生 
+ [Xfire文件读取漏洞](http://www.anquan.us/static/bugs/wooyun-2016-0166751.html)
+ [Revisting XXE and abusing protocols](https://sensepost.com/blog/2014/revisting-xxe-and-abusing-protocols/)老外写的真难读，xxe+expect=RCE
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)

## JSONP注入
## SSTI
## 代码执行 / 命令执行
## 文件包含
+ [**链家旗下自如某站一个有意思的文件包含到简单内网渗透（本地文件包含getshell技巧）**](https://shuimugan.com/bug/view?bug_no=134185)**包含临时文件getshell技巧+内网渗透**
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
+ [从开源中国的某XXE漏洞到主站shell](https://shuimugan.com/bug/view?bug_no=59911)
## 文件上传 / 解析漏洞
+ [快钱某站上传Getshell](https://shuimugan.com/bug/view?bug_no=209324)上传图片处，直接上传jsp shell,利用00截断绕过。
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [酷我音乐某处任意文件上传Getshell](https://shuimugan.com/bug/view?bug_no=214510)扫描c段,发现文件上传，getshell.扫描内网，代理访问内网存活ip，又发现内网中一处文件上传
+ [顺丰某分站从列目录到代码执行Getshell](https://shuimugan.com/bug/view?bug_no=59911)扫描c段,发现列目录漏洞，下载服务dll，反编译,发现密码，写一个客户端程序，调用服务上传,getshell
+ [趣网某漏洞Getshell导致所有站点/数据库沦陷（涉及435W+用户数据/68W+交易订单)](https://shuimugan.com/bug/view?bug_no=5991)IOS APP在头像上传处修改上传类型后可上传php shell
+ [广州长城宽带OA系统任意文件上传已入远程桌面泄漏大量办公信息](https://shuimugan.com/bug/view?bug_no=213240)后台管理系统弱口令，登录后写邮件处发现fckeditor上传，getshell,netstat -abn 发现termsrv（远程桌面）端口位于25608，添加用户并连接
+ [中国民航某内部系统Getshell(泄漏9K多员工信息)](https://shuimugan.com/bug/view?bug_no=213106)爆破登录，头像上传处上传shell,菜刀连接找到数据库配置
+ [21英语网存在两处漏洞导致getshell/ROOT权限/影响大量子站点](https://shuimugan.com/bug/view?bug_no=213058)图片上传,木马前面添加GIF89a文件头+00截断,成功getshell
+ [运营商安全之中国移动多个漏洞打包(可SHELL内网漫游)](https://shuimugan.com/bug/view?bug_no=212792)上传图片处，抓包修改后缀绕过,getshell.
+ [奔驰某站getshell涉及大量数据库](https://shuimugan.com/bug/view?bug_no=212604)弱口令登陆,上传视频处，getshell
+ [**七牛云存储某站漏洞可跨越边界漫游内网**](https://shuimugan.com/bug/view?bug_no=212372)**github泄露测试账号，登录发现一些ip,nmap扫描端口找到一处web应用:ITDB资产管理系统,官网下源码找到默认数据库路径，进而直接下载数据库,数据库中发现管理员口令。登录发现上传文件处存在漏洞，上传文件getshell,文件路径通过审计源码得知.剩下的就是内网渗透部分.**
+ [中国联通某系统存在任意文件上传漏洞可越权修改28W商户信息数10W资质文件](https://shuimugan.com/bug/view?bug_no=212079)发布活动处，可上传图片。getshell
+ [建设银行某分行系统漏洞导致GetShell](https://shuimugan.com/bug/view?bug_no=210956)扫描端口获取商户后台,注册后添加信息上传(jspx)
+ [海尔集团某服务器配置不当导致代码执行](https://shuimugan.com/bug/view?bug_no=210602)访问/robots.txt/a.php,发现robots.txt被当成php文件执行，存在nginx解析漏洞
+ [TOM在线某分站任意文件上传可导致Getshell](https://shuimugan.com/bug/view?bug_no=210421)头像上传php shell
+ [梅花网某分站任意代码上传webshell及多库30W用户可查](https://shuimugan.com/bug/view?bug_no=209677)发稿时可上传文件,上传aspx shell
+ [满堂红集团任意文件上传可Getshell泄漏企业内部信息以及Blind XXE](https://shuimugan.com/bug/view?bug_no=214735)googlehacking到上传页面，上传shell
+ [酷狗主站的一处任意文件上传可shell](https://shuimugan.com/bug/view?bug_no=208816)上传php文件瞬间会被删除，利用条件竞争，在被删除之前生成一个shell
+ [新浪乐居某处缺陷导致内网漫游](https://shuimugan.com/bug/view?bug_no=208792)
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀
+ [财政部某站任意文件上传](https://shuimugan.com/bug/view?bug_no=214735)附件上传处,抓包改后缀


## 逻辑漏洞
## 弱口令
+ [运营商安全之中国移动多个漏洞打包(可SHELL内网漫游)](https://shuimugan.com/bug/view?bug_no=212792)扫描端口,发现一处jboss后台匿名访问，弱口令登陆。
## 其他漏洞
### RPO(relative path overwrite)
### Web Cache
### redis
## PHP相关
### 弱类型
### 随机数问题
### 伪协议
### 序列化
### php mail header injection
### 其他
## java-Web
### 反序列
### Struct2
## python-Web
## Node-js
# 渗透测试

