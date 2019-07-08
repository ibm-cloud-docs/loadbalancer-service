---

copyright:
  years: 2017, 2018
lastupdated: "2019-02-19"

keywords: updates, additions, imporvements

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

# IBM Cloud Load Balancer の最近の更新
{: #recent-updates-for-ibm-cloud-load-balancer}

IBM© Cloud Load Balancer の新機能と更新された機能について説明します。

## 2019 年 2 月
{: #february-2019}

### データ・ログ
{: #data-logs}

IBM Cloud Load Balancer は、データ・ログの転送をサポートするようになりました。データ・ログが有効になっている場合、ロード・バランサーのログ・データは [IBM Cloud Log Analysis サービス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/log-analysis){:new_window} に転送されます。顧客は、データ・ログを [IBM Cloud Log Analysis サービス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/log-analysis){:new_window} から表示できます。

## 2018 年 12 月
{: #december-2018}

### バックエンド暗号化およびデータ・ログ転送
{: #backend-encryption-and-data-log-forwarding}

IBM Cloud Load Balancer は、バックエンド暗号化と、データ・ログの転送機能をサポートするようになりました。 バックエンド暗号化により、終端間でのデータ・トラフィック (ロード・バランサーとバックエンド・サーバーの間のトラフィックを含む) を暗号化できます。 データ・ログの転送により、ロード・バランサーから IBM Bluemix Log Analysis Service にデータ・ログを送信できます。

## 2018 年 8 月
{: #august-2018}

### レイヤー 7 サポート
{: #layer-7-support-1}

IBM Cloud Load Balancer は、レイヤー 7 ロード・バランシングをサポートするようになりました。 レイヤー 7 (L7) サポートにより、トラフィックを URL に転送するか、拒否するか、または、ベアメタル・サーバーおよび仮想サーバー・インスタンスを含む L7 プール・メンバーに分散することができます。 着信データ・トラフィックは、レイヤー 7 ポリシーおよびルールを使用して分類されます。 ポリシーは、データ・トラフィックがポリシーに関連付けられたルールに一致した場合に実行されるアクションを定義します。

追加の詳細については、[レイヤー 7 ロード・バランシング](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing)を参照してください。

## 2018 年 4 月
{: #april-2018}

### 水平スケーリング
{: #horizontal-scaling}

IBM Cloud Load Balancer は、負荷の増大時に自動的に拡大し、負荷の減少時に縮小するようになりました。 ロード・バランサーは、作成時点では 2 つのアプライアンスで開始しますが、モニタリング・システムが負荷の増大を検知すると、アプライアンスの数は (当文書の作成時点で) 16 まで増加する可能性があります。 各アクティブ・アプライアンスの IP アドレスは、DNS A レコードとしてロード・バランサーの完全修飾ドメイン・ネーム (FQDN) に追加されます。

### 内部ロード・バランサー
{: #internal-load-balancer-1}

需要の高い「内部」バージョンの IBM Cloud Load Balancer が使用可能になりました。 このロード・バランサーはパブリックには公開されませんが、それでも、(例えば図に示すような多層デプロイメントの) IBM Cloud プライベート・ネットワーク内でアプリケーションのバランスを取るために使用できます。

![内部ロード・バランサー](./images/InternalLB.png)

また、パブリック・サイドの IBM Cloud Load Balancer の旧バージョンに対してセキュアであり、かつ整合性もあります。

### メトリックのモニタリング
{: #monitoring-metrics-2}

「IBM Cloud Monitoring」サービスを活用して、ご使用のロード・バランサーおよびアプリケーションに関連付けられた以下のパフォーマンス・メトリックをモニターできるようになりました。

* スループット
* 接続率
* アクティブ接続数

![メトリックのモニタリング](./images/Metrics.png)

最大 2 週間分のサンプルが収集され、ロード・バランサーの Web UI によって表示されます。 また、このデータは IBM Cloud Monitoring サービスのポータルでも表示できます。 2 週間を超える期間のデータが必要な場合、Cloud Monitoring インスタンスに送信する他のクラウド・メトリックのボリュームによっては、モニタリング・プランをアップグレードする必要が生じる場合があります。 追加の詳細については、[モニタリング・メトリック](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer)を参照してください。

この機能では、いくつかの[単純なステップ](/docs/account?topic=account-unifyingaccounts)によって、IBM Cloud IaaS と PaaS のアカウントをリンクする必要があります。

### 暗号スイートのカスタマイズ
{: #cipher-suite-custom-1}

ロード・バランサーが SSL 終端処理を行うよう構成されている場合に使用される暗号スイートをカスタマイズできるようになりました。

IBM Cloud Load Balancer での SSL 終端処理を (フロントエンド・プロトコルとして **HTTPS** を選択することによって) 有効にすると、セキュリティーのベスト・プラクティスに合致する、慎重に選択された暗号スイートのデフォルト・セットが使用可能になります。 IBM は、新たに検出される可能性のある脆弱性を厳重に監視し続け、このリストを適宜更新します。 この対応は、ソフトウェアおよびハードウェア・コンポーネントのシームレスなセキュリティーの更新と共に、お客様のアプリケーションを常にセキュアな状態に保ちます。

追加の詳細については、[カスタムの暗号スイート](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application)に関するセクションを参照してください。
