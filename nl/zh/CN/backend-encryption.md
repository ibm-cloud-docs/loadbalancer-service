---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

keywords: encryption, security

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# 设置后端加密
{: #setting-backend-encryption}

支持后端加密以允许端到端数据流量加密。不仅负载均衡器与客户机之间的流量会加密，而且负载均衡器与后端服务器之间的流量也会加密。

要启用后端加密：

* 如果添加新的 HTTPS 协议，请将前端和后端设置为 **HTTPS**。
* 对于现有的 HTTPS 协议，请将后端设置为 **HTTPS**。
