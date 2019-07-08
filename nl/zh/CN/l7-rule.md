---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, rules, traffic

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

# 第 7 层规则
{: #layer-7-rules}

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
