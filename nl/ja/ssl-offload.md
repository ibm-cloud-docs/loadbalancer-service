---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: ssl, offload, cipher, suite

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

# IBM Cloud Load Balancer での SSL オフロード
{: #ssl-offload-with-ibm-cloud-load-balancer}

すべての着信 HTTPS 接続について、ロード・バランサー・サービスは SSL 接続を終了し、バックエンド・サーバーとのプレーン・テキスト HTTP 通信を確立します。 CPU 集中型の SSL ハンドシェークおよび暗号化/復号のタスクはバックエンド・サーバーから移行され、アプリケーション・トラフィックの処理にすべての CPU サイクルを使用できます。

ロード・バランサーが SSL オフロード・タスクを実行するには、SSL 証明書が必要です。 既存の SSL 証明書を使用するか、新しい SSL 証明書を購入し、[IBM© Cloud 証明書ストア ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/classic/security/sslcerts){:new_window} を介して管理できます。

## SSL 暗号スイート
{: #ssl-cipher-suites}

ロード・バランサー・サービスは、SSL オフロードのある TLS バージョン 1.2 をサポートしています。

次の SSL 暗号はご使用のロード・バランサーによりサポートされています。

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

ロード・バランサーに 1 つ以上の HTTPS フロントエンド・アプリケーション・ポート (プロトコル) が構成されている場合、デフォルトで上記のすべての事前定義済み SSL 暗号がそのロード・バランサーで使用可能になります。

必要な場合、ご使用のロード・バランサー用に異なる SSL 暗号を使用可能にすることを選択できます。詳しくは、[HTTPS アプリケーション用の優先暗号スイートの選択](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application)を参照してください。
{: note}
