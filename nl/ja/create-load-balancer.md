---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: create, new, load balancer

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

# IBM Cloud Load Balancer の作成
{: #creating-an-ibm-cloud-load-balancer}

IBM© Cloud Load Balancer サービスを作成するには、以下の手順を実行します。

1. ブラウザーから、[カスタマー・ポータル![外部リンク・アイコン](../../icons/launch-glyph.svg "")](https://control.softlayer.com/){: new_window}を開き、アカウントにログインします。

2. **「カタログ」**をクリックし、「インフラストラクチャー」セクションから、**「ネットワーク」 > 「ロード・バランサー」**と進みます。

	<img src="images/catalog-load-balancer.png" alt="描画" style="width: 600px;"/>

3. **「IBM Cloud Load Balancer」** (デフォルト選択) を選択し、**「作成」**をクリックします。

	**「作成」**ではなく**「アップグレード」**が表示される場合、[これらのステップ](/docs/account?topic=account-unifyingaccounts)に従って、IBM Cloud Infrastructure (SoftLayer) アカウントをリンクする必要があります。

	<img src="images/create-load-balancer.png" alt="描画" style="width: 600px;"/>

4. **「データ・センター」**ドロップダウンから適切なデータ・センターを選択し、情報を確認してから**「次へ」**をクリックします。

	<img src="images/select-datacenter.png" alt="描画" style="width: 600px;"/>

5. ロード・バランサー・タイプを指定します。

	パブリック・インターネットへのアクセスを必要とするインターネット向けアプリケーションの場合、**「パブリック (インターネット向け)」**を選択します。

	<img src="images/select-lb-type.png" alt="描画" style="width: 600px;"/>

	デフォルトでは、パブリックなロード・バランサーは、グローバルに固有のパブリック IP アドレスを IBM グローバル・アドレス・プールから受け取ります。 しかし、お客様自身のアドレス・プールからのパブリック・アドレスを割り当てたい場合、または、アカウント内のファイアウォール・サービスの背後にデプロイしたい場合は、自身のパブリック・サブネットに[十分な IP アドレス](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting)があるかどうかを確認し、**「アカウント内のパブリック・サブネットから割り振る (Allocate from a public subnet in your account)」**を選択してください。

	パブリック・インターネットへのアクセスを必要としない内部専用アプリケーションの場合、**「内部 (プライベート) (Internal (Private))」**タイプを選択します。

	<img src="images/lb-type-private.png" alt="描画" style="width: 500px;"/>

	ロード・バランサーのタイプがインターネット向けと内部のどちらであっても、ロード・バランサーのデプロイ先としてアカウント内のいずれかのプライベート・サブネットを選出してください。 このサブネットからアプリケーション・サーバーに到達可能である必要があります。 必要な場合は、適切なネットワーク接続を保証するために VLAN スパンニングを有効にしてください。

	プライベート・サブネットが表示されない場合は、**「前へ」**をクリックし、プライベート・サブネットのある別のデータ・センターを選択してください。

6. **「次へ」**をクリックして、構成を終了します。

## 次に行うこと
{: #whats-next-2}
[基本パラメーター](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters)を使用してロード・バランサーを構成します。
