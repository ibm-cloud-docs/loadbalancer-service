---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: create, use, elastic

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

# 柔軟なサーバー・ロード・バランシングのための {{site.data.keyword.loadbalancer_full}} の使用
{: #creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing}

{{site.data.keyword.loadbalancer_full}} サービスは、お客様のビジネスに不可欠なアプリケーションの拡張容易性および可用性を高めるのに役立ちます。 このサービスは、アプリケーション・サーバーの正常性をモニターし、スマートなロード・バランシング方式を活用して複数サーバー間でトラフィックを分散させ、システム容量を動的に調整することで変化するトラフィック負荷を処理します。

## このガイドで達成できること
{: #what-you-ll-accomplish-2}

このステップバイステップ・ガイドでは、サービスを構成する方法を学ぶことができます。   

Cloud Load Balancer の注文について詳しくは、[開始](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)を参照してください。
{: note}

タスク  | 説明
------------- | -------------
[基本パラメーターの構成](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters) | ロード・バランサーを構成します。
[アプリケーション・リソースの識別](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources) | 起点プールやヘルス・チェック・メカニズムなど、アプリケーションのリソースを識別します。
[ロード・バランサーの検討と注文](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order) | 注文の内容を検討した後、発注します。
[サービスのモニターと管理](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service) | 構成を編集し、サービスのパフォーマンスをモニターします。
