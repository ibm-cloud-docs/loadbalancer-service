---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# 关于

IBM Cloud Load Balancer 服务通过在多个应用程序服务器实例之间分配流量，仅将流量转发给运行状况良好的实例，来帮助客户改进其业务关键应用程序的可用性。

## 功能概述
IBM Cloud Load Balancer 服务提供以下功能：

* 公用（面向互联网）负载均衡器
	* 可通过其标准域名 (FQDN) 公开访问的服务
	* 专用子网上的后端服务器实例
* 内部负载均衡器
	* 可通过其标准域名 (FQDN) 专用访问的服务
	* 客户请求通过专用网络进行路由
	* 专用子网上的后端服务器实例
* 基本负载均衡
	* 基于层 4 应用程序端口信息进行流量分配
	* 支持基于 HTTP、HTTPS 和 TCP 的应用程序 
	* 各种负载均衡方法，如循环法 (RR)、加权循环法和最少连接数
	* 在位于数据中心本地的虚拟服务器和裸机计算实例之间进行负载均衡
* 服务器运行状况检查
	* 定期监视服务器运行状况，以确保流量仅转发给运行状况良好的服务器 
	* 对 TCP 端口进行层 4 运行状况检查，对 HTTP 端口进行层 7 运行状况检查 
* SSL 卸载
	* 使用与后端服务器的明文 HTTP 通信，终止入局 SSL (HTTPS) 流量
* 高级流量管理
	* 客户机吸引力（会话持久性）
	* 每个虚拟端口的最大连接数
* 使用直观图形界面和 API 轻松进行管理
* 内置可靠性 
* 按使用量定价 
* 监视
    * 监视用户指定的时间间隔期间 HTTP、HTTPS 和 TCP 协议的吞吐量、活动连接数和连接速率度量值。请参阅[监视度量值](monitoring-metrics.html)获取更多详细信息。
* 第 7 层支持
    * HTTP/HTTPS 流量将路由到基于 HTTP 头的不同后端服务，并使用策略和规则来完成。规则基于 HTTP 头字段，用于对流量进行分类。流量与所有规则匹配时，将执行策略指定的操作。    
