---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: resources, server, application, instance, configure

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

# アプリケーション・サーバーのリソースの識別
{: #identifying-your-application-server-resources}

最下部にある表から**サーバー・インスタンス**を見つけて **+** をクリックして、それらをロード・バランサーの背後に置きます。 アカウント内の IBM© Cloud 仮想サーバー・インスタンス (VSI) およびベアメタル・サーバーから選択できます。

これらのサーバー・インスタンスは、ロード・バランサー・サービスをデプロイするデータ・センターにローカルでなければなりません。 さらに、同じ都市にある近隣データ・センターからのサーバー・インスタンスも追加することができます (例えば、データ・センター名の先頭 3 文字が同じである場合)。

<img src="images/locate-server-instance.png" alt="描画" style="width: 300px;"/>

**「次へ」**をクリックします。

サーバーの**重み**が関係するのは、ロード・バランシング方式として**重みづけしたラウンドロビン**を使用している場合のみです。 デフォルトの重みは 50 であり、範囲は 0 から 100 です。 他ロード・バランシング方式の場合は重みはぼかし表示されます。
{: note}

アプリケーション・サーバー数の最大数制限について詳しくは、[アプリケーション・サーバー数の制限](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-)に関する箇所を参照してください。
{: tip}

## 次に行うこと
{: #what-s-next-3}
注文の[内容を検討](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order)してから、注文します。
