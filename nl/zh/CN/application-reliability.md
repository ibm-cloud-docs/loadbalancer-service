---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 通过 IBM Cloud Internet Services 的全局负载均衡提升应用程序的可靠性和可扩展性
如果您有电子商务 Web 站点，或者正在托管需要可由最终用户随时进行访问的应用程序，那么您可能比较关注应用程序的全天候可用性和性能。 

IBM Cloud Internet Services (CIS) 提供的全局负载均衡功能有助于提升应用程序的可靠性和可扩展性，同时尽可能提供最佳的最终用户体验。本指南提供全局负载均衡配置的预评估。  

## 您将完成的内容

在此分步指南中，您将学会如何配置类似于下面所演示内容的设置。

<img src="images/Reliability1.png" alt="图样" style="width: 300px;"/>

此示例中，应用程序资源将部署在两个数据中心位置中，一个在美国西部，另一个在美国东海岸。最终用户可能从世界各地访问此应用程序。 

任务 |描述 
------------- | -------------
[创建 CIS 实例](create-cis.html) | 首先，使用 IBM 客户门户网站创建 IBM Cloud Internet Services (CIS) 实例
。
[输入有关域的信息](input-domain.html) | 输入您要保护并为其提供全局负载均衡的域的信息。
[开始配置全局负载均衡器](begin-config.html) | 开始配置全局负载均衡器。
[识别应用程序资源](identify-app-resources.html) | 识别应用程序资源，例如源池和运行状况检查机制。
[定义全局负载均衡器](define-global-lb.html) | 通过指定主机名、添加和调整源池以及定义其他规则来控制如何将流量提供给客户机，从而定义您的全局负载均衡器配置。
