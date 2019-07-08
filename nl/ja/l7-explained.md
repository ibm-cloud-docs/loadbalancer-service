---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policies, rules, pools

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

# レイヤー 7 ロード・バランシング
{: #layer-7-load-balancing}

IBM© Cloud Load Balancer サービスは、レイヤー 7 (アプリケーション層) データを使用して、複数のサーバー・インスタンス (ベアメタル・サーバーおよび仮想サーバー・インスタンスを含む) 間でトラフィックを分散させます。

 * 分散されるデータ・トラフィックは、ポリシーおよびルールを使用して分類されます。
 * ポリシーに関連付けられたすべてのルールにデータ・トラフィックが一致した場合に実行されるアクションがポリシーで定義されます。
 * レイヤー 7 (L7) ロード・バランシングは、HTTP および HTTPS トラフィックに対してのみサポートされています。

## レイヤー 7 ポリシーおよびルール
{: #layer-7-policies-and-rules}
レイヤー 7 ポリシーはフロントエンド・アプリケーション・ポートと関連付けられます。 複数のポリシーを 1 つのフロントエンド・ポートと関連付けることができます。

 * これらのポリシーは、各ポリシーに割り当てられた優先順位に基づいて順に評価されます。
 * ポリシーが一致すると、関連付けられたアクションが実行されます。
 * 各 L7 ルールは 1 つのポリシーと関連付けられます。
 * 1 つのポリシーに関連付けられたすべてのルールが `true` と評価された場合、そのポリシーは一致したことになり、関連付けられたアクションが実行されます。

追加の詳細については、[L7 のポリシーおよびルール](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy)を参照してください。

## レイヤー 7 プール
{: #layer-7-pools}
各レイヤー 7 ロード・バランサー・プールには、1 つ以上の論理サーバー・インスタンスが含まれます。

 * 各論理サーバー・インスタンスは、IP アドレスとポート番号によって識別されます。
 * 各プールにはヘルス・モニターが関連付けられていて、そのヘルス・モニターがプール内のすべてのサーバーの正常性をモニターします。
 * セッション・パーシスタンス用にプールを構成できます。
 * セッション・パーシスタンスを構成するには、クライアントのソース IP アドレスを使用します。

追加の詳細については、[L7 プール](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool)を参照してください。
