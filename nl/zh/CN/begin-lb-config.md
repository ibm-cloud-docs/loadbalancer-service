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

# 配置 IBM Cloud Load Balancer 参数
{: #configuring-ibm-cloud-load-balancer-parameters}

创建 Load Balancer 后，可以对其进行配置以实现弹性负载均衡。为此，请执行以下操作：

1. 命名 Load Balancer，并可选择添加描述。

	<img src="images/lb-config-basic.png" alt="图样" style="width: 300px;"/>

2. 通过识别应用程序在侦听的协议和端口，输入应用程序概要文件的详细信息。您可以对前端和后端使用相同的配置，也可以公开不同的前端端口（例如，出于安全目的）。

3. 缺省负载均衡方法为**循环法**。根据您的应用程序需求，可以从下拉列表中将其更改为**加权循环法**或**最少连接数**。

4. （可选）可以启用**会话吸引力**。如果启用此选项，那么来自给定最终用户（例如，使用相同源 IP 的用户）的所有请求在系统定义的“吸引力”时间内都将转至同一后端服务器。

5. 您还可以对应用程序设置**最大连接数限制**。

6. 单击**添加协议**以指定应用程序可能在侦听的其他端口和协议。请确保所有前端端口都是唯一的。您可以选择 HTTP、HTTPS 或 TCP 作为前端协议。

	<img src="images/lb-add-protocol.png" alt="图样" style="width: 300px;"/>

	在初始配置时最多可以定义 2 个端口。日后创建服务实例后可添加更多端口。请参阅[端口数限制](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-)，以获取有关允许的最大端口数的更多信息。
{:note:}

7. 如果选择后端协议为 HTTP，那么 IBM© Cloud Load Balancer 会终止入局 HTTPS（基于 SSL 的 HTTP）连接，可以通过明文 HTTP 与后端应用程序服务器通信，并从服务器卸载处理器密集型 SSL 任务。如果选择的后端协议为 HTTPS，那么 Load Balancer 与后端服务器之间的流量将会加密。您必须上传 SSL 证书。从下拉列表中选择一个可用的证书。  

	<img src="images/lb-ssl-cert.png" alt="图样" style="width: 300px;"/>

	如果您没有现有证书，请单击**添加新证书**。这会将您转至 IBM Cloud 证书服务，您可以在其中购买新证书或上传现有证书。 
	
	添加证书后，返回到负载均衡器配置页面，然后单击“SSL 证书”下拉列表下面的“刷新”图标以查看并添加新上传的证书。

	<img src="images/order-ssl-cert.png" alt="图样" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="图样" style="width: 300px;"/>

	**注：切勿删除与 HTTPS 侦听器关联的任何证书，因为这可能会导致功能方面的问题。**

8. 单击**下一步**。

## 配置运行状况检查
对于每个应用程序端口，必须定义运行状况检查。这些是先前基本配置菜单中确定的后端端口。

<img src="images/config-health-check.png" alt="图样" style="width: 300px;"/>

系统会为这些后端端口预填充缺省运行状况检查配置。您可以定制以下设置来满足您的应用程序需求。

* **时间间隔**：两次连续的运行状况检查尝试之间的时间间隔（以秒为单位）
* **超时**：系统将等待针对运行状况检查请求的响应的最长时间量
* **最大尝试次数**：系统在声明端口运行状况欠佳之前，将另外尝试进行运行状况检查的最大次数。
* **路径**：运行状况检查的 HTTP URL 路径。     

单击**下一步**以启用选项。

## 接下来做什么
[识别应用程序资源](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources)，例如源池和运行状况检查机制。
