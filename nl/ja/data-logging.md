---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# データ・ロギング
{: #data-logging}

データおよびヘルス・チェックのログは、デバッグと保守を行うのに役立ちます。データ・ロギング機能が有効になっている場合、IBM ロード・バランサーは、これらのログをアカウントの [IBM Cloud Log Analysis サービス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://logging.ng.bluemix.net){:new_window} に転送します。

この機能は、以下のように有効または無効にすることができます。

* 新規のロード・バランサーを作成して、この機能をオンに設定する。
* API `enableOrDisableDataLogs` を使用する。

## IBM Cloud Logging Analysis サービスでのログの表示
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

顧客の IBM Cloud アカウントを使用して [IBM Cloud Logging Analysis サービス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://logging.ng.bluemix.net){:new_window}にログインします。ログは Kibana から表示できます。詳しくは、[このトピック](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana)を参照してください。

データ・ログは、Softlayer と IBM Cloud アカウントがリンクされている場合にのみ送信されます。Softlayer アカウントに関連付けられている IBM Cloud アカウントを選択してから、Kibana ダッシュボードにログインします。
{: tip}

## ログ出力の例
{: #log-output-examples}

以下の出力は {{site.data.keyword.loadbalancer_full}} データ・ログの例です。

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` はロード・バランサー名であり、`dal09` はデータ・センターです。
* `323698` はアカウント ID です。`643866` はロード・バランサー ID です。`713576` はメンバー ID です。
* `xxx.xxx.xxx.xxx` は GDPR 用にマスクされたパブリック IP です。

以下の出力は、IBM Cloud Logging Analysis Service 内のヘルス・チェック・ログの例です。

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` はメンバー IP アドレスです。
* `682175` はメンバー ID です。
