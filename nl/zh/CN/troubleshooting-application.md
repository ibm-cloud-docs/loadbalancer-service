---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 应用程序服务器故障诊断
{: #application-server-troubleshooting}

本主题提供有关使用 Load Balancer 时可能会遇到的常见问题的信息。

## 后端服务器运行状况欠佳
如果后端服务器的运行状况在衰退，请尝试验证以下列表以尝试解决此问题：

* 配置的后端协议的端口与应用程序正在侦听的端口相匹配吗？
* 配置的运行状况检查是否具有正确的协议（TCP 或 HTTP）、端口和 URL（对于 HTTP）信息？对于 HTTP，确保应用程序对配置的运行状况检查 URL 的响应为 `200 正常`。
* 后端服务器与 Load Balancer 位于不同子网上吗？如果位于不同子网上，请确保启用 VLAN 生成。
* 后端服务器是具有已启用的安全组的虚拟服务器吗？如果是，请确保安全组规则允许 Load Balancer 与虚拟服务器之间的流量。
