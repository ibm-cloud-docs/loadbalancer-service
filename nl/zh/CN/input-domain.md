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

# 输入有关域的信息
输入有关您要保护并为其提供全局负载均衡的域的信息。

1. 单击“入门”屏幕左侧的**概述**。输入域名（或子域名），并单击**添加域**。 
    
    <img src="images/Reliability3.png" alt="图样" style="width: 300px;"/>
    
    **注：**IBM Cloud Internet Service 不是 DNS 注册器，因此必须先前已经创建此域（或子域）。

    在“服务详细信息”部分下，您会注意到，新添加的域将初始显示为“暂挂”状态。 

    <img src="images/Reliability4.png" alt="图样" style="width: 300px;"/>    

2. 导航到具有相应的 DNS 注册器的域的管理页面，通过定义 NS 记录将域/子域委派给 IBM 名称服务器。

您可能必须等待最多 24 小时，让信息在 DNS 数据库中复制。完成后，您的域状态将更改为“活动”。 

<img src="images/Reliability5.png" alt="图样" style="width: 300px;"/>    
