---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: limitations, problems, troubleshooting

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

# {{site.data.keyword.loadbalancer_full}} 的已知问题和限制
{: #known-issues-and-limitations-with-ibm-cloud-load-balancer}

本主题提供 {{site.data.keyword.loadbalancer_full}} 服务当前已知问题和限制的相关信息。

## 已知问题
{: #known-issues}
{{site.data.keyword.loadbalancer_full}} 服务目前具有以下问题：

* 小 - 服务器实例和协议选项卡中的**编辑**按钮适用于所有条目，而不是限制到使用复选框选择的行上。
* 小 - 在初始创建 Load Balancer 服务期间，如果您在各个屏幕之间来回切换，您将丢失定制运行状况检查设置。
* 小 - 使用 Internet Explorer 11、Edge 或 Safari 浏览器来管理 Load Balancer 服务时，可能会遇到一些问题。作为替代方法，请使用 Firefox 或 Chrome 浏览器。
* 表面 - 初始服务创建期间，数据中心的下拉列表可能会扭曲。不管怎样，您仍可以选择想要的数据中心。
* 表面 - 复查页面上的定价信息舍入为两位小数位数。对于正确的定价，请参阅套餐页面显示的定价。

## 已知限制
{: #known-limits}
{{site.data.keyword.loadbalancer_full}} 服务目前具有以下限制：

* 虚拟端口/协议的最大数目 - 10
* Load Balancer 背后的服务器数目 - 50
