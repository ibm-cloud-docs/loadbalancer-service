---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 探索 Load Balancer

IBM Cloud 提供了数个可选择的负载均衡解决方案。下表对负载均衡解决方案进行了比较，以帮助您选择适合的解决方案。要了解各个产品的更多信息，请单击表中的名称。 

滚动到右侧以查看表的其余部分！


|        |[IBM Cloud Load Balancer](../../infrastructure/loadbalancer-service/getting-started.html#getting-started)|[本地 Load Balancer](../../infrastructure/local-load-balancer/getting-started.html#getting-started)（共享）|[本地 Load Balancer](../../infrastructure/local-load-balancer/getting-started.html#getting-started)（专用）|[Citrix NetScaler](../../infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX（标准）|[Citrix NetScaler](../../infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX（白金）|
|------- | :------: | :------: | :------: | :------: | :------: |
|**公共 VIP**|是|是|是|是|是|
|**专用 VIP**|是|否|是|是|是|
|**第 4 层 LB**|是|是|是|是|是|
|**第 7 层 LB**|是|Cookie 持久性|Cookie 持久性|是|是|
|**运行状况检查**|是|是|是|是|是|
|**水平伸缩**|是|否|否|否|否|
|**SSL 卸载**|是|是|是|是|是|
|**管理**|通过 IBM 门户网站|通过 IBM 门户网站|通过 IBM 门户网站|自我管理（供应商 GUI）|自我管理（供应商 GUI）|
|**高可用性**|内置|内置|可选|可选|可选|
|**预先 LB（TCP 优化、压缩、高速缓存和 WAF）**|否|否|否|受限制|是|
|**全局 LB (GLB)**|否|否|否|否|是|
|**定价**|按使用量|每月固定|每月固定|每月固定|每月固定|
