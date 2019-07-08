---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policy, policies

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}
{:tip: .tip}

# 第 7 层策略
{: #layer-7-policy}

第 7 层 (L7) 策略用于通过将其 L7 信息与 L7 规则相匹配来对流量进行分类，然后在这些规则匹配时执行特定操作。

* 策略应用于前端应用程序端口（协议）。
* 多个策略可以应用于同一协议。

由于可以将多个策略应用于一个协议，因此有优先级与每个策略相关联。

* 将首先对优先级设置为最低的策略求值。
* 如果该策略的关联规则与流量不匹配，那么将对优先级列表中的下一个优先级最低的策略求值。

如果流量与任何策略规则都不匹配，那么会将流量重定向到缺省池，缺省池是部署基本 Load Balancer 时配置的池。

每个策略都与某个操作相关联，该策略中的所有规则都与流量匹配时会执行该操作。

操作可以是：

- 拒绝
- 重定向到 URL
- 重定向到池

将首先对设置为`拒绝`的策略求值，而不考虑这些策略的优先级。

在此之后，将对设置为`重定向到 URL` 的策略求值。

最后，将对设置为`重定向到池`的策略求值。

在每个操作类别中，会按优先级升序（从最低到最高）对策略求值。

## 第 7 层策略属性
{: #layer-7-policy-properties}

属性|描述 
------------- | -------------
名称 |策略的名称。每个策略都必须具有唯一名称。
操作|规则匹配时要执行的操作。操作为 `REJECT`、`REDIRECT_URL` 和 `REDIRECT_POOL`。首先对其操作设置为 `REJECT` 的策略求值，而不考虑该策略的优先级。接着对其操作设置为 `REDIRECT_URL` 的策略求值，最后对其操作设置为 `REDIRECT_POOL` 的策略求值。
优先级|将根据优先级升序对策略求值。
重定向 URL|操作设置为 `REDIRECT_URL` 时，流量将重定向到的 URL。
重定向 L7 池|操作设置为 `REDIRECT_POOL` 时，将向其发送流量的服务器池。
协议|应用策略的前端应用程序端口。

## 第 7 层规则
{: #layer-7-rule}
第 7 层规则定义入局流量中要与特定值匹配的部分。

* 如果入局流量与规则的指定值匹配，那么规则求值为 `true`。
* 第 7 层规则始终与第 7 层策略相关联。多个第 7 层规则可以与同一个第 7 层策略相关联。
* 如果多个规则与一个策略相关联，那么每个规则会求值为 `true` 或 `false`。
* 如果与一个策略关联的所有规则均求值为 `true`，那么会将该策略的操作应用于请求。否则，Load Balancer 会对下一个策略求值。

规则具有类型，可以是：

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

这些类型指示第 7 层流量中要与规则匹配的部分。

类型|要抽取并求值的字段
----------| -----------------------
`HOST_NAME`|URL 的主机名部分（例如，`api.my_company.com`）
`FILE_TYPE`|URL 的结尾，表示文件类型（例如，`jpg`）
HEADER|HTTP 头中的字段
COOKIE|HTTP 头中指定的 cookie
PATH|URL 中主机名之后的部分（例如，`/index.html`）

规则还具有比较类型，用于指示如何对规则求值。 
规则可以具有以下比较类型：

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

比较类型|求值类型
----------------|---------------------
`REGEX`|将抽取的字段（例如，`hostname`）与提供的正则表达式相匹配
`STARTS_WITH`|验证抽取的字段是否以提供的字符串开头
`ENDS_WITH`|验证抽取的字段是否以提供的字符串结尾
`CONTAINS`|验证抽取的字段是否包含提供的字符串
`EQUAL_TO`|验证抽取的字段是否与提供的字符串完全相同

并非所有规则类型都支持所有比较类型。例如，如果使用的是 `FILE_TYPE`，那么最好使用比较类型 `REGEX` 和 `ENDS_WITH`。
{: tip}

## 第 7 层规则属性
{: #layer-7-rule-properties}

属性|描述 
------------- | -------------
类型|指定规则的类型。规则类型可以是 `HOST_NAME`（主机的名称）、`FILE_TYPE`（文件的类型）、`HEADER`（头）、`COOKIE` (cookie) 或 `PATH`（路径）。
比较类型|比较类型与规则类型、键和值一起关联使用，用于定义规则和对流量分类。比较类型可以是：`REGEX`、`STARTS_WITH`、`ENDS_WITH`、`CONTAINS` 和 `EQUAL_TO`。
键|规则类型 `HEADER` 和 `COOKIE` 的描述键。
值|对于规则类型 `HEADER` 和 `COOKIE`，会将值与键进行比较。
反转|如果将值设置为 1，那么每当与指定的规则不匹配时，此 L7 规则比较的值都将设置为 `true`。
第 7 层策略标识|规则连接到的策略的唯一标识。
