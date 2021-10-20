# Banli

Banli是一款简单好用的高危资产和高危漏洞扫描工具！本项目也是自己在深入学习Go语言后计划陆续发布的项目之一。项目暂不考虑开源，因为代码写的还不完美。本项目仅用于安全研究人员在授权的情况下使用，请遵守网络安全法，若因本工具产生任何问题，后果请自负，与作者无关！程序代码中不会添加任何形式的后门，运行程序一般情况下不会对系统产生危害，请各位师傅放心使用！本项目会持续更新，直到海枯石烂。

本项目创建于2021年10月16日，最近一次更新时间为2021年10月20日。

- [0x01-基本介绍](https://github.com/Goqi/Banli#0x01-%E5%9F%BA%E6%9C%AC%E4%BB%8B%E7%BB%8D)
- [0x02-设计思路](https://github.com/Goqi/Banli#0x02-%E8%AE%BE%E8%AE%A1%E6%80%9D%E8%B7%AF)
- [0x03-使用说明](https://github.com/Goqi/Banli#0x03-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
- [0x04-资产列表](https://github.com/Goqi/Banli#0x04-%E8%B5%84%E4%BA%A7%E5%88%97%E8%A1%A8)
- [0x05-更新记录](https://github.com/Goqi/Banli#0x05-%E6%9B%B4%E6%96%B0%E8%AE%B0%E5%BD%95)
- [0x06-未来计划](https://github.com/Goqi/Banli#0x06-%E6%9C%AA%E6%9D%A5%E8%AE%A1%E5%88%92)
- [0x07-参考资源](https://github.com/Goqi/Banli#0x07-%E5%8F%82%E8%80%83%E8%B5%84%E6%BA%90)

## 0x01-基本介绍

我们有一只比熊犬，她的名字叫板栗。她时而很活泼，时而又很安静，像极了这个Banli。因为活泼，所以她可以高效快速的进行高危资产识别和高危漏洞扫描。因为安静，所以她的动静很小尽可能的不被安全设备发现。Banli可以很方便的对内网或外网的高危资产，高危漏洞进行扫描。方便渗透测试和红队评估人员进行快速识别高危资产，快速利用高危漏洞，从而最终拿到系统权限！

## 0x02-设计思路

Banli要解决的问题是如何快速识别企业的高危资产，如何快速扫描企业的高危漏洞。包括Web资产、中间件资产、框架资产、安全设备等高危资产的识别，包括Web漏洞、命令执行漏洞、反序列化等高危漏洞的扫描。项目设计时考虑到了尽可能的避免触发安全告警。设计思路包括多利用404页面，少用特定的后台等敏感页面等。具体的设计实现方式后续会公开！

## 0x03-使用说明

程序设计时遵循简单原则。项目尽可能的去掉了用户可控参数，因此很多参数用户无法自定义。资产识别功能都是对当前路径的urls.txt文件进行扫描。漏洞扫描模块都是对资产识别之后自动生成的文件进行扫描。例如：通过命令Banli.exe is seeyon扫描Seeyon资产，若有，则存在的结果会记录在isSeeyon.txt文件中，之后直接使用Banli.exe hack seeyon即可对Seeyon资产进行Seeyon漏洞扫描。减少无用功，拒绝无效努力！

- 程序目前有如下功能：
  - **资产识别**
    - 所有资产扫描：Banli.exe isall
    - 内网资产扫描：Banli.exe isnei
    - 外网资产扫描：Banli.exe iswai
    - 单个高危资产扫描：Banli.exe is shiro
  - **漏洞扫描**
    - 单个漏洞全部资产扫描：Banli.exe hack seeyon
  - **信息收集**
    - title获取：Banli.exe title

- 运行程序，查看帮助信息：Banli.exe help

  ```
  D:\Go\src\Banli>go run Banli.go help
  程序作者:0e0w
  程序名称:Banli(v0.5)
  开发时间:2021年10月20日
  程序说明:一款简单好用的高危资产和高危漏洞扫描工具！
  请在当前目录创建urls.txt文件进行资产识别或扫描！！！
  
  Usage:
    Banli [flags]
    Banli [command]
  
  Available Commands:
    completion  generate the autocompletion script for the specified shell
    hack        Scan single vulnerabilities.
    help        Help about any command
    is          Scan single assets.
    isall       Scan all assets.
    isnei       Scan Intranet assets.
    iswai       Scan Extranet assets.
    title       Get assets title.
  
  Flags:
    -h, --help   help for Banli
  
  Use "Banli [command] --help" for more information about a command.
  程序运行完成！运行时间:14.15ms
  ```


## 0x04-资产列表

​	目前支持识别的资产：后期会定期进行更新！

- 通达OA、蓝凌OA、Shiro、Weblogic、Seeoyon、ThinkPHP、万户OA、phpMyAdmin、Coremail、红帆OA、ActiveMQ、Axis2、宝塔面板、ElasticSearch、帆软报表、Hadoop。

## 0x05-更新记录

- 2021年10月20日：添加单个资产的扫描方式。例：Banli.exe is thinkphp
- 2021年10月19日：支持Title扫描。支持内网资产和外网资产分开扫描。
- 2021年10月18日：添加新的资产识别，Chestnut更名为Banli。
- 2021年10月17日：优化程序，支持扫描单个资产列表，加入漏洞扫描功能。
- 2021年10月16日：项目框架基本完成。

## 0x06-未来计划

- urls.txt去重。内网存活资产发现。
- 资产识别漏洞扫描之后将结果发送到指定邮箱。
- 加入账号密码爆破功能。

## 0x07-参考资源

- https://golang.org

[![Stargazers over time](https://starchart.cc//Goqi/Banli.svg)](https://starchart.cc/Goqi/Banli)