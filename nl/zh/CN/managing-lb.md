---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 监视和管理服务
您可以通过单击 Load Balancer 摘要页面上的服务名称 URL 来编辑配置或监视服务性能。 

Load Balancer 服务实例的**标准域名 (FQDN) 地址**会显示在服务名称的正下方。最终用户可以通过此 FQDN 地址连接到您的应用程序。请注意，Load Balancer 服务的公共和专用 IP 地址不会对外公开；只会公开 FQDN 地址。 

<img src="images/fqdn-address.png" alt="图样" style="width: 300px;"/>

**概述**选项卡提供了服务的高级状态信息。此选项卡显示应用程序服务器及其端口的当前运行状况。此外，还提供了系统性能的快速摘要 - 吞吐量、连接速率、并发连接数等。 

浏览至**监视**选项卡可查看系统性能的实时图表。可以按各个应用程序端口和各种持续时间来查看这些图形。 

<img src="images/monitor-lb.png" alt="图样" style="width: 300px;"/>

您可以通过浏览至**协议**、**服务器实例**和**运行状况检查**选项卡来编辑现有配置。例如，浏览至“协议”选项卡可定义其他应用程序端口或定制 SSL 密码列表。 

<img src="images/protocols-monitor.png" alt="图样" style="width: 300px;"/>
