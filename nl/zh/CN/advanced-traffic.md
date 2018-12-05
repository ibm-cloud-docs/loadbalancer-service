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

# 高级流量管理
本节讨论随 Load Balancer 服务一起提供的几个高级流量管理功能。

## 最大连接数

使用“最大连接数”配置，可以针对给定前端虚拟端口，限制并行连接的最大数目。缺省情况下，不会指定任何限制。针对跨所有前端虚拟端口的某个给定前端虚拟端口或系统范围的最大可能并行连接数为 15000。  

## 会话持久性

Load Balancer 基于连接的 `source IP` 针对给定 VIP 端口，支持会话持久性。举例来说，如果针对端口 80 (HTTP) 启用会话持久性，那么来自相同客户机的后续 HTTP 连接尝试会在相同的后端服务器上实现持久性。此功能可用于所有三种支持的协议（HTTP、HTTPS 和 TCP）。

Load Balancer 最多支持 10,000 个客户机持久性条目。这些条目的到期时间为 10 分钟。10 分钟后，从相同客户机接收的其他请求可能会转发到不同的后端服务器。如果会话持久性条目未到期，但是后端端口运行状况变得欠佳，那么会选择新的服务器，用于转发任何后续客户机连接。  

## HTTP 保持活动
只要在客户机和后端服务器上启用 `HTTP 保持活动`，Load Balancer 即支持该功能。Load Balancer 尝试复用服务器端 HTTP 连接，来增加连接的有效性并减少等待时间。

## 连接超时数
Load Balancer 使用以下超时值。目前不能定制这些值。

|名称 |描述 |超时 |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
|服务器端连接尝试   |Load Balancer 可以用于建立与后端服务器的 TCP 连接的最大时段。如果连接尝试成功，那么 Load Balancer 将根据所配置的负载均衡方法，尝试下一个可用服务器。|5 秒   |
|客户机端空闲连接  |最大空闲时间，在该时间后，Load Balancer 将关闭客户机端连接（如果客户机无法正常关闭其连接）。|50 秒  |
|服务器端空闲连接  |最大空闲时间（TCP 的后端协议配置），在该时间后，Load Balancer 将关闭服务器端连接。使用 HTTP 的后端协议配置，如果 Load Balancer 无法在空闲超时时段内接收其 HTTP 请求的响应，它将向终端客户机返回错误消息。 |50 秒  |
{: caption="表 1. Load Balancer 超时值" caption-side="top"} 

## 保留终端客户机 IP 地址 

Load Balancer 作为逆向代理运作，可从客户机终止入局流量。它会使用自己的 IP 地址，建立与后端服务器实例的个别连接。对于与后端服务器的 HTTP 连接（针对前端 HTTP 或 HTTPS 连接），Load Balancer 将通过在 `X-Forwarded-For HTTP` 头中包含原始客户机 IP 地址来保留该地址。对于 TCP 连接，不会保留原始客户机 IP 信息。
