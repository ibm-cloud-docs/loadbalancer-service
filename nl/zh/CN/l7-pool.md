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

# 第 7 层池
{: #layer-7-pool}

第 7 层 (L7) 池是用于处理入局请求的服务器（成员）的逻辑分组。

第 7 层负载均衡功能可以根据策略和规则将入局流量定向到不同后端池。通过将多个 L7 池与负载均衡器相关联来支持此功能。第 7 层池与第 7 层策略（其操作是`重定向到池`）配合使用。

L7 池仅支持 HTTP 作为后端协议。

## 会话持久性
可以为每个第 7 层池配置会话持久性。有关更多详细信息，请参阅  
[高级流量](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer)部分。

## 第 7 层成员

与第 7 层池关联的后端服务器称为第 7 层成员。

通过每次指定不同的端口号，可以将同一后端服务器多次添加到 L7 池。

## 配置运行状况检查
对于每个第 7 层池，必须定义运行状况检查。系统会预填充 L7 池的缺省运行状况检查配置。

您可以定制以下设置来满足您的应用程序需求：

 * **Interval**：两次连续的运行状况检查尝试之间的时间间隔（以秒为单位）
 * **Timeout**：系统将等待对运行状况检查请求的响应的最长时间量。
 * **MaxRetries**：系统在声明服务运行状况欠佳之前，将另外尝试进行运行状况检查的最大次数。
 * **UrlPath**：第 7 层运行状况检查的 HTTP URL 路径。
