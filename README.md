# Banli-高危资产识别和高危漏洞扫描

![Banli](https://socialify.git.ci/Goqi/Banli/image?description=1&font=Bitter&forks=1&issues=1&name=1&owner=1&pattern=Floating%20Cogs&pulls=1&stargazers=1&theme=Light)

Banli是一款极其简单好用的高危资产识别和高危漏洞扫描利用工具。本项目也是自己深入学习理解Go语言后陆续发布的项目之一。**本项目仅限用于安全研究人员在授权的情况下使用，请遵守网络安全法，若因本工具产生任何问题，后果请自负，与作者无关！** 程序代码中绝不会添加任何形式的后门，运行程序一般情况不会对目标系统产生危害，请各位师傅放心使用！**本项目会持续更新，直到海枯石烂。**  作者：[0e0w](https://github.com/0e0w)

本项目创建于2021年10月16日，最近一次更新时间为2022年8月15日。**每月15日定期更新！**

- [01-Banli基本介绍](https://github.com/Goqi/Banli#01-Banli%E5%9F%BA%E6%9C%AC%E4%BB%8B%E7%BB%8D)
- [02-Banli设计思路](https://github.com/Goqi/Banli#02-Banli%E8%AE%BE%E8%AE%A1%E6%80%9D%E8%B7%AF)
- [03-Banli使用说明](https://github.com/Goqi/Banli#03-Banli%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
- [04-Banli更新记录](https://github.com/Goqi/Banli#04-Banli%E6%9B%B4%E6%96%B0%E8%AE%B0%E5%BD%95)
- [05-Banli未来计划](https://github.com/Goqi/Banli#05-Banli%E6%9C%AA%E6%9D%A5%E8%AE%A1%E5%88%92)
- [06-感谢参考项目](https://github.com/Goqi/Banli#06-%E6%84%9F%E8%B0%A2%E5%8F%82%E8%80%83%E9%A1%B9%E7%9B%AE)

## 01-Banli基本介绍

我们养了一只比熊犬，她的名字叫板栗。她时而很活泼，时而又很安静，像极了这个Banli。

- **因为活泼**，所以她可以高效快速的进行高危资产识别和高危漏洞扫描。
- **因为安静**，所以她的动静很小尽可能的不被流量监测等安全设备发现。

Banli可以对内外网的系统进行高危资产识别和高危漏洞扫描。方便渗透测试和红队评估人员进行快速识别高危资产，快速利用高危漏洞，从而最终拿到系统权限！

## 02-Banli设计思路

Banli要解决的问题是如何快速识别企业的高危资产，如何快速扫描企业的高危漏洞。包括Web资产、中间件资产、框架资产、安全设备等高危资产的识别，包括Web漏洞、命令执行漏洞、反序列化等高危漏洞的扫描。项目设计时考虑到了尽可能的避免触发安全告警。设计思路包括多利用404页面，少用特定的后台等敏感页面等。具体的设计实现方式后续会公开！

程序文件说明：

- Banli.ini 全局参数设置
- ips.txt 单个存活的ip
- ipc.txt 内网存活的IP网段
- urls.txt 单个Web资产
- user.txt 爆破时的用户名字典
- pass.txt爆破时的密码字典
- dnslog.txt dnslog地址
- Banlilogs.txt 程序运行日志

## 03-Banli使用说明

程序设计时遵循简单原则。本项目没有用户可控参数，**所有参数用户都无法自定义**。必要修改的参数可以通过修改当前目录下配置文件Banli.ini进行设置。扫描结果可自动打包发送到邮箱！

**1、资产识别模块都是对当前路径的urls.txt文件进行扫描，支持多种URL格式，一行一个，结尾不能有/号，不能存在无效的URL格式！否则会影响程序的识别效果，或直接导致程序无法运行！**

**2、漏洞扫描模块都是对资产识别之后自动生成的文件进行扫描。** 例如：通过命令Banli.exe is seeyon扫描Seeyon资产，如果存在Seeyon资产，则自动创建isSeeyon.txt文件。之后可以使用Banli.exe hack seeyon对isSeeyon.txt文件内的资产进行Seeyon漏洞扫描。**减少无用功，拒绝无效努力！**

**3、信息收集模块支持网站Title扫描。** 后期支持端口扫描和资产发现功能！

**4、密码爆破模块目前支持大多数的可爆破服务。**

**5、被动扫描加爬虫扫描是一款扫描器的最后追求！** 

**一、资产识别**

- 说明：设计初衷是对单个高危资产进行扫描，一次性扫描多个资产效率较低。
- 支持识别的资产应用：activemq、ax2、baota、cas、confluence、coremail、dcuz、druid、dubbo、elasticsearch、exchange、eyoumail、finereport、flink、gerapy、gitlab、gogs、hadoop、harbor、hongfanoa、jboss、jeecms、jellyfin、jenkins、jinheroa、jira、jumpserver、jupyter、kibana、kingdee、kylin、landrayoa、leagsoft、liferay、metabase、mobileiron、nacos、ofbiz、phpmyadmin、rabbitmq、saltstack、seeyon、shiro、skywalking、solr、sonarqube、spark、springboot、struts、swagger、thinkphp、tomcat、tongdaoa、vesystem、vmware、wanhuoa、weaveroa、weblogic、websphere、yapi、yonyou、zabbix、zentao。等
- 资产支持列表：Banli.exe is
- 所有资产扫描：Banli.exe is all
- OA 资产扫描：Banli.exe is oa
- 内网资产扫描：Banli.exe is nei
- 外网资产扫描：Banli.exe is wai
- 单个高危资产扫描：Banli.exe is log4j
  - 使用Banli.exe is log4j扫描那些组件资产用到了log4j。运行结束后存在的资产会保存到对应的文件中。

**二、漏洞扫描**

漏洞扫描模块将是Banli的重点，目前支持的资产较少。后期将重点更新漏洞扫描模块！

- 支持扫描的框架漏洞：seeyon、druid、weblogic、log4j、grafana、apisix、spring。
- 所有资产全部漏洞扫描：Banli.exe hack god 该功能待公开
- 单个漏洞全部资产扫描：Banli.exe hack seeyon
- **支持漏洞** ：Banli.exe hack log4j
  - 将Banli.ini文件中的dnslog值替换成自己的地址。扫描完成后在自己的dnslog上面看记录。

  - Banli.exe hack log4j

    扫描特定资产的Log4j2漏洞。目前支持：Druid、Flink、JSPWiki、OFBiz、SkyWalking、Solr、Struts2、CAS、MonbileIro User Portal、Seeyon、Unifi Network、VMware HCX、VMware Horizon、VMware NSX、VMware vCenter、VMware vRealize、VMware Workspace One、Zipkin

  - Banli.exe hack log4j fuzz

    测试urls.txt文件中HTTP头是否存在漏洞。此模块将会发送大量的请求包。

  - Banli.exe hack log4j scan d:/

    扫描本地目录的代码中是否存在危险的log4j框架。结果保存到output文件夹内。
- **支持漏洞** ：Banli.exe hack thinkphp
  
  - 目前支持26个Thinkphp的不同版本的漏洞。
- **支持漏洞** ：Banli.exe hack weblogic

**三、信息收集**

- [x] **获取资产title** ：Banli.exe get title
- 程序自动对urls.txt内的资产进行title扫描。

- [x] **获取资产js文件** ：Banli.exe get js
- 程序自动对urls.txt内的资产进行js文件的扫描。

- [x] **获取存活网段** ：Banli.exe get ipc 默认tcp扫描
- 程序自动获取内网中存活的网段。一行一个存活的C段，保存到output/ipc.txt
  - Banli.exe get ipc tcp
  - Banli.exe get ipc icmp
  - Banli.exe get ipc ping
  - Banli.exe get ipc udp
  - Banli.exe get ipc arp
- [ ] **获取存活IP** ：Banli.exe get ips 待实现
- 获取内网中存活的单个IP地址。一行一个地址保存到ips.txt
- [x] **获取Web资产** ：Banli.exe get urls
- 程序自动对ips.txt内的ip资产进行Web资产探测。支持IP段。
- [ ] **Web路径扫描** ：Banli.exe get path 待实现。后续通过[路婧](https://github.com/Goqi/Lujing)完整实现。
  - Banli.exe get path

**四、密码爆破**

- Banli.exe is crack
  - 扫描IP可以进行爆破的高危端口。请将ip资产保存到ips.txt，一行一个。
- Banli.exe crack
  - 对isCrack.txt内的资产进行默认端口密码爆破。例:127.0.0.2:22。目前支持：FTP、SSH、MsSQL、MySQL、PostgreSQL、MongoDB。用户名和密码字典为crackuser.txt和crackpass.txt

**五、被动扫描**

- 被动扫描的设计思路是拦截请求，修改请求，重发数据。支持HTTPS扫描，程序第一次运行后自动生成证书，需要在浏览器中设置代理并导入证书。默认代理IP端口为127.0.0.1:8715
- Banli.exe pass log4j
  - 勉强能用，速度奇慢。

**六、爬虫扫描**

- 目前不支持。

## 04-Banli更新记录

- 2022年8月15日：1.HTTP请求全部换成了fasthttp。目前来看，比原生http效率确实提升不少。2.新增get js模块。可以识别urls.txt资产中的js文件。参考了[URLFinder](https://github.com/pingc0y/URLFinder)，感谢pingc0y。3.更新log4j漏洞扫描模块，支持1000多个HTTP头的fuzz，实际测试效果还不错。4.新增socks5和http代理模式。在Banli.ini中配置。
- 2022年7月15日：1.新增邮件发送功能，程序每次执行后都将output压缩并发送到邮件，邮箱信息在Banli.ini里面配置。2.更新内网存活资产网段探测。Banli.exe get ipc。3.新增网站备份文件扫描。Banli.exe get bak。4.新增运行程序时会判断是否存在Bnali.ini，若不存在则自动创建。5.更新了几个OA的漏洞扫描。6.将结果输出保存到output文件夹里。新建input文件夹，里面包含程序的默认执行文件。7.程序执行前自动对urls.txt和ips.txt资产进行去重操作。8.对程序进行了大量的优化更新。
- 2022年6月15日：1.新增Banli.ini配置文件，可自定义部分参数。感谢@FR33D0M提供的折中思路。2.添加Log4j漏洞的被动扫描。3.新增Banli.exe get urls。可扫描ips.txt内的Web资产。4.新增Confluence CVE-2022-26134及其他俩个CVE漏洞扫描。5.新增MS17010漏洞概念扫描。
- 2022年5月15日：1.支持vmware 3个漏洞扫描。2.支持solr 4个漏洞扫描。3.支持spring 4个漏洞扫描。4.支持Thinkphp 18个漏洞扫描。5.支持Shiro-550 key识别漏洞扫描，Shiro-550 exp扫描（暂不公开）。6.更新22个组件的log4j漏洞扫描。7.更新优化web识别。8.添加其他的漏洞扫描。9.更新如果执行hack命令时没有对应的资产则自动执行is模块。
- 2022年4月15日：1.增加高危爆破端口扫描、增加密码爆破功能。2.新增多个资产识别。3.新增18个Log4j2相关组件的漏洞扫描（Banli.exe hack log4j2）。4.程序大量优化，优化识别规则多线程等问题。
- 2022年4月8日：今天本程序被一些微信群推荐，感谢。优化程序，更新代码逻辑。
- 2022年2月15日：1.修复默认线程数太高导致内存指针报错的问题，添加用户可自定义线程数，感谢@T-T。
  2.支持单个资产的识别，感谢@ᗡD。v0.91版本暂时不对外公开！
- 2022年1月15日：添加随机UserAgent。添加日志记录。添加APISIX漏洞扫描模块。
- 2021年12月15日：新增37个资产识别。支持log4j、grafane、weblogic等部分漏洞扫描识别。完善优化程序，去除https证书过期导致无法识别的问题等。发布v0.8版本。
- 2021年11月15日：支持Seeyon漏洞扫描。添加新的资产识别。优化程序，发布v0.7版本。
- 2021年10月29日：添加支持新的资产识别，优化程序。发布v0.6版本。
- 2021年10月20日：添加单个资产的扫描方式。例：Banli.exe is thinkphp
- 2021年10月19日：支持Title扫描。支持内网资产和外网资产分开扫描。
- 2021年10月18日：添加新的资产识别，Chestnut更名为Banli。
- 2021年10月17日：优化程序，支持扫描单个资产列表，加入漏洞扫描功能。
- 2021年10月16日：项目框架基本完成。

## 05-Banli未来计划

- [ ] 程序日志记录功能不够完善，后续更新！
- [ ] 爆破时若字典文件不存在，则自动创建字典文件。
- [ ] 支持所有漏洞一键扫描。
- [ ] crack模块爆破互联网时指针错误，该bug待更新。
- [ ] 对输出结果进行优化，支持输出到excel文件。
- [ ] 添加代理池自动收集实现匿名扫描。
- [ ] 更新WEB框架！
- [x] 添加支持代理扫描。支持HTTP代理和socks5代理。
- [x] 优化不同操作系统下的漏洞验证。
- [x] 对扫描的结果进行压缩加密保存。
- [x] 添加敏感路径爆破收集功能。添加资产发现模块。
- [x] urls.txt去重。内网存活资产发现。
- [x] 资产识别或漏洞扫描之后将结果发送到指定邮箱。
- [x] ips.txt支持C段B段模式。
- [x] 添加高危漏洞被动扫描功能！！！
- [x] 将结果输出到output文件夹内。
- [x] ms17010支持IP段扫描。
- [x] 程序在运行前自动创建Banli.ini文件。

## 06-感谢参考项目

本项目开发过程中参加了这些项目的代码思路或漏洞详情等！感谢这些作者，感谢开源社区！
- https://github.com/veo/vscan
- https://github.com/JKme/cube
- https://github.com/r0eXpeR/fingerprint
- https://github.com/0x727/FingerprintHub
- https://github.com/shmilylty/netspy
- https://github.com/achuna33/MYExploit
- https://github.com/Threekiii/Awesome-POC

## Stargazers

[![Stargazers @Goqi/Banli](https://reporoster.com/stars/Goqi/Banli)](https://github.com/Goqi/Banli/stargazers)

## Forkers

[![Forkers @Goqi/Banli](https://reporoster.com/forks/Goqi/Banli)](https://github.com/Goqi/Banli/network/members)

![](Banli/wx.png)

[![Stargazers over time](https://starchart.cc//Goqi/Banli.svg)](https://starchart.cc/Goqi/Banli)