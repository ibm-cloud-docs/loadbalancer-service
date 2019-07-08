---

copyright:
  years: 2018
lastupdated: "2018-11-21"

keywords: error, message, troubleshooting, problems

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

# 错误消息故障诊断
{: #error-message-troubleshooting}

本主题提供有关在创建/更新 IBM© Cloud Load Balancer 实例时可能会遇到的常见错误消息的信息。

|错误|说明|解决方案|
| ------------- | ------------- | ----- |
|`已达到最大 `n` 个 Load Balancer。`|每个帐户只允许有 50 个 Load Balancer 实例。|确保每个帐户的 Load Balancer 实例数不超过 50 个。|
|`Load Balancer 产品订单中已达到最大 `n` 个给定协议。`|供应 Load Balancer 时，只能添加 2 个协议。|如果需要更多协议，在供应后，可以在 Load Balancer 管理流中的**协议**选项卡中最多添加 10 个协议。有关更多信息，请参阅[监视和管理服务](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)。|
|`Load Balancer 产品订单中已达到最大 `n` 个给定服务器实例。`|供应 Load Balancer 时，只能添加 10 台服务器。|如果需要更多服务器，在供应后，可以在 Load Balancer 管理流中的**服务器实例**选项卡中最多添加 50 个实例。有关更多信息，请参阅[监视和管理服务](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)。|
|`Load Balancer 名称必须为字符串，并且必须至少包含 1 到 40 个字符。`|Load Balancer 名称是必需的。请仅对名称使用字母数字字符（或特殊字符“-”和“.”）。名称不得以特殊字符开头或结尾，并且长度必须限制为 40 个字符。|请输入唯一的 Load Balancer 名称。例如，“ui-servers”或“backend-servers”。|
|`在给定的 Load Balancer 名称中发现格式错误。`|Load Balancer 名称是必需的。请仅对名称使用字母数字字符（或特殊字符“-”和“.”）。名称不得以特殊字符开头或结尾，并且长度必须限制为 40 个字符。|请输入唯一的 Load Balancer 名称。例如，“ui-servers”或“backend-servers”。|
|`已存在同名（不区分大小写）的 Load Balancer。`|已存在同名的 Load Balancer。|请输入唯一的 Load Balancer 名称以继续操作，例如，“ui-servers”或“backend-servers”。|
|`Load Balancer 描述必须是字符串，并且不能超过 255 个字符。`|Load Balancer 描述必须是不超过 255 个字符的字符串。|请将描述限制为 255 个字符以内。|
|`前端端口 80 已被使用。`|您可能输入了已在使用的前端端口。|请输入唯一的前端端口。|
|`后端端口必须为整数。`|您可能输入了无效的后端端口值。|请输入 1 和 65535 之间的后端端口号。|
|`由于协议和端口在运行状况监视器中不可编辑，因此无法通过 UI 处理此错误。`|您的专用子网不属于标准类型，无法用于创建 Load Balancer。|请联系 IBM 支持人员。|
|`专用子网 `xyz` 必须至少具有 `n` 个可用 IP 地址。`|所选专用子网没有任何可用的 IP 地址。|请查看这些[故障诊断步骤](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting)以获取更多信息。|
|`指定的专用子网 VLAN 位于路由器 `xyz` 上。但是，在同一路由器上找不到具有 `n` 个可用 IP 的公用 VLAN。`|发生这种情况的原因是，您在供应期间选择了**从此帐户的公用子网分配**选项。|请改为选择**从 IBM 系统池分配**或联系 IBM 支持人员。|
|`指定的专用子网 VLAN 位于路由器 `xyz` 上。但是，在同一路由器上的 VLAN 中找不到具有 `n` 个可用 IP 的公用子网。`|发生这种情况的原因是，您在供应期间选择了**从此帐户的公用子网分配**选项。|请改为选择**从 IBM 系统池分配**或联系 IBM 支持人员。|
|`给定的新描述必须是字符串。`|您可能输入了无效的描述。|请输入有效 Load Balancer 描述，不超过 255 个字符。|
|`需要计费项目才能处理针对 uuid=aaaa-bbbb-cccc-dddd 的 Load Balancer 的取消操作。`|帐单信息缺失或对您的帐户无效，因此无法取消 Load Balancer。|请联系 IBM 支持人员。|
|`发生内部错误。无法检索数据。`|无法检索度量值数据|请重新装入页面。如果问题仍然存在，请联系 IBM 支持人员。|
|`前端端口必须是 1 到 65535 之间的整数，不包括范围 56500-56520。`|您可能输入的是 56500-56520 之间的前端端口号。|请输入 1 到 65535 之间的唯一端口号，但不包括范围 56500 到 56520。|
|`后端端口必须为整数。`|您可能输入了无效的后端端口值。|请输入 1 和 65535 之间的后端端口号。|
|`后端端口必须是 1 到 65535 之间的整数，不包括范围 56500-56520。`|您可能输入的是 56500 和 56520 之间的后端端口。|请输入 1 和 65535 之间的后端端口号，但不包括范围 56500 到 56520。|
|`后端协议 HTTP 与前端协议 TCP 不兼容。`|您可能选择了不兼容的后端协议和前端协议组合。|请选择有效的前端和后端协议组合，格式如下：`<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
|`为成员 abcd-xxxx-yyyy-2222 提供了成员权重 <some value>。允许的权重值为 0-100`|您可能输入了无效的权重。|请输入 0 和 100 之间的权重值。|
|`访存服务器时发生问题。`|发生网络超时问题会导致出现此问题。|请重新装入页面。如果问题仍然存在，请联系 IBM 支持人员。|
