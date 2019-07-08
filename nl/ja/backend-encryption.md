---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

keywords: encryption, security

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

# バックエンド暗号化の設定
{: #setting-backend-encryption}

バックエンド暗号化は、終端間でのデータ・トラフィックの暗号化を可能にするためにサポートされています。 ロード・バランサーと暗号化クライアントの間のトラフィックだけではなく、ロード・バランサーとバックエンド・サーバーの間のトラフィックも対象となります。

バックエンド暗号化を有効にするには、次のようにします。

* 新しい HTTPS プロトコルを追加する場合、フロントエンドとバックエンドを **HTTPS** に設定します。
* 既存の HTTPS プロトコルの場合、バックエンドを **HTTPS** に設定します。
