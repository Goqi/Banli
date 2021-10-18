# Chestnut

Chestnut(板栗)是一款简单好用的高危资产和高危漏洞扫描工具！

本项目是深入学习Go语言后计划陆续发布的项目之一。项目暂不考虑开源，因为代码写的太烂。本项目仅用于安全研究人员在授权的情况下使用，请遵守网络安全法，若因本工具产生任何后果请自负，与作者无关！程序不会添加任何形式的后门，运行程序不会对系统产生危害，请各位师傅放心使用！

本项目创建于2021年10月16日，最近一次更新时间为2021年10月18日。

- [0x01-基本介绍](https://github.com/0e0w/Chestnut#0x01-%E5%9F%BA%E6%9C%AC%E4%BB%8B%E7%BB%8D)
- [0x02-设计思路](https://github.com/0e0w/Chestnut#0x02-%E8%AE%BE%E8%AE%A1%E6%80%9D%E8%B7%AF)
- [0x03-使用说明](https://github.com/0e0w/Chestnut#0x03-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
- [0x04-资产列表](https://github.com/0e0w/Chestnut#0x04-%E8%B5%84%E4%BA%A7%E5%88%97%E8%A1%A8)
- [0x05-更新记录](https://github.com/0e0w/Chestnut#0x05-%E6%9B%B4%E6%96%B0%E8%AE%B0%E5%BD%95)
- [0x06-参考资源](https://github.com/0e0w/Chestnut#0x06-%E5%8F%82%E8%80%83%E8%B5%84%E6%BA%90)

## 0x01-基本介绍

​	我们有一只比熊犬，她的名字叫板栗。她时而很活泼，时而又很安静，像极了这个Chestnut。因为活泼，所以她可以高效快速的进行高危资产识别和高危漏洞扫描。因为安静，所以她的动静很小尽可能的不被安全设备发现。Chestnut可以很方便的对内网或外网的高危资产，高危漏洞进行扫描。方便渗透测试和红队评估人员进行快速识别高危资产，快速利用高危漏洞，从而最终拿到系统权限！

## 0x02-设计思路

​	Chestnut要解决的问题是如何快速识别企业的高危资产，如何快速扫描企业的高危漏洞。包括Web资产、中间件资产、框架资产、安全设备资产的识别等，包括Web漏洞、。项目设计时考虑到了尽可能的避免触发安全告警。设计思路包括多利用404页面，少用特定的后台等敏感页面等。具体的设计实现方式后续会公开！

## 0x03-使用说明

​	本工具适用于甲方乙方安全人员对资产目标的快速发现与识别。方便快速发现资产挖掘漏洞实现财富自由或是更快速的发现存在漏洞的资产从而成为一名优秀的打工人。

- 运行程序，查看帮助信息：Chestnut.exe help

  ```
  程序作者:0e0w 
  程序名称:板栗Chestnut(v0.2) 
  开发时间:2021年10月17日 
  程序说明:一款简单好用的高危资产和高危漏洞扫描工具！ 
  请在当前目录创建urls.txt文件进行资产识别扫描！！！！
  
  Usage:
    Chestnut [flags]
    Chestnut [command]
  
  Available Commands:
    completion  generate the autocompletion script for the specified shell
    expall      Scan all vulnerabilities.
    expseeyon   Scan seeyon all vulnerabilities.
    help        Help about any command
    isall       Scan all assets.
    isseeyon    Scan Seeyon assets.
    isshiro     Scan Shiro assets.
    isweblogic  Scan Weblogic assets.
  
  Flags:
    -h, --help   help for Chestnut
  
  Use "Chestnut [command] --help" for more information about a command.
  程序运行完成！运行时间:13.5079ms
  ```

- 运行程序，扫描全部资产：Chestnut.exe isall

  ```
  程序作者:0e0w 
  程序名称:板栗Chestnut(v0.2) 
  开发时间:2021年10月17日 
  程序说明:一款简单好用的高危资产和高危漏洞扫描工具！ 
  ################### 开始识别Coremail资产！###############
  资产总数: 99 个
  程序用时: 20.0099854 s
  
  ################### 开始识别Shiro资产！#################
  资产总数: 99 个
  程序用时: 20.1962996 s
  
  程序运行完成！运行时间:20.5079ms
  ```

- 运行程序，扫描单个资产：Chestnut.exe isshiro
- 运行程序，扫描ThinkPHP漏洞：Chestnut.exe hackthinkphp
- 运行程序，扫描Seeyon漏洞：Chestnut.exe hackseeyon

## 0x04-资产列表

​	目前支持识别的资产：后期会定期进行更新！

- 通达OA、蓝凌OA、Shiro、Weblogic、Seeoyon、ThinkPHP、万户OA、phpMyAdmin、Coremail。

## 0x05-更新记录

- 2021年10月17日：优化程序，支持扫描单个资产列表，加入漏洞扫描功能。
- 2021年10月16日：项目框架基本完成。

## 0x06-参考资源

- https://golang.org