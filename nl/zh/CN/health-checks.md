---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: health check, http, tcp, ports

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 使用 IBM Cloud Load Balancer 执行运行状况检查
{: #performing-health-checks-with-ibm-cloud-load-balancer}

对于每个后端应用程序端口来说，必须具有运行状况检查定义。运行状况检查配置下的端口和协议必须与所定义的后端端口和协议相匹配，否则会拒绝该配置。

Load Balancer 会定期执行运行状况检查，以监视后端端口的运行状况，并相应地将客户机流量转发给它们。如果发现给定后端服务器端口运行状况欠佳，那么不会向其转发新连接。Load Balancer 会继续监视这些运行状况欠佳的端口的运行状况，如果发现端口的运行状况变得良好，两个连续运行状况检查尝试都成功传递，那么会恢复其使用。

针对 HTTP、HTTPS 和 TCP 端口执行运行状况检查如下所示：

* **HTTP：**针对预先指定 URL 的 `HTTP GET` 请求会发送到后端服务器端口。在收到 `200 OK` 响应时，会将服务器端口标记为运行状况良好。通过 GUI 的缺省 `GET` URL 为“/”，可以对其进行定制。

* **HTTPS：**只有当后端加密已启用且后端协议设置为 HTTPS 时才适用。除所有运行状况检查消息都是 SSL 加密外，该机制与 **HTTP** 相同。有关后端加密的更多信息，请参阅 /docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-setting-backend-encryption

* **TCP：**Load Balancer 尝试在指定 TCP 端口上打开与后端服务器的 TCP 连接。如果连接尝试成功，则会将服务器端口标记为运行状况良好，然后关闭连接。

	缺省运行状况检查时间间隔为 5 秒，针对运行状况检查请求的缺省超时为 2 秒，而重试尝试的缺省次数为 2 次。
  {: note}
