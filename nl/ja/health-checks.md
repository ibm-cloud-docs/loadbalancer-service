---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: health check, http, tcp, ports

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

# {{site.data.keyword.loadbalancer_full}} でのヘルス・チェックの実行
{: #performing-health-checks-with-ibm-cloud-load-balancer}

ヘルス・チェックの定義は、それぞれのバックエンド・アプリケーション・ポートで必須です。 ヘルス・チェック構成に含まれるポートとプロトコルは、定義されているバックエンドのポートとプロトコルに一致している必要があります。さもないと、構成は拒否されます。

ロード・バランサーは定期的にヘルス・チェックを実行して、バックエンド・ポートの正常性をモニターし、それに応じてそれらにクライアント・トラフィックを転送します。 指定されたバックエンド・サーバー・ポートが正常でないことが検出されると、そのポートには新しい接続は転送されません。 ロード・バランサーはそれらの正常でないポートのモニターを続行し、連続する 2 回のヘルス・チェック試行を正常に渡すことによりそれらが再び正常な状態であることが検出されると、それらの使用を再開します。

HTTP ポート、HTTPS ポート、および TCP ポートに対するヘルス・チェックは、以下のように実行されます。

* **HTTP:** 事前指定 URL に対する `HTTP GET` 要求がバックエンド・サーバー・ポートに送信されます。 `200 OK` 応答を受信すると、サーバー・ポートに正常のマークが付けられます。 デフォルトの `GET` URL は、GUI を介した「/ 」で、カスタマイズ可能です。

* **HTTPS:** バックエンド暗号化が有効でバックエンド・プロトコルが HTTPS に設定されている場合にのみ適用可能です。ヘルス・チェック・メッセージがすべて SSL 暗号化されることを除き、メカニズムは **HTTP** と同じです。バックエンド暗号化について詳しくは、/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-setting-backend-encryption を参照してください。

* **TCP:** ロード・バランサーは、指定された TCP ポートでバックエンド・サーバーとの TCP 接続をオープンします。 接続試行が成功するとサーバー・ポートに正常のマークが付けられ、それから接続がクローズされます。

	デフォルトのヘルス・チェック間隔は 5 秒、ヘルス・チェック要求に対するデフォルト・タイムアウトは 2 秒、そしてデフォルトの再試行回数は 2 回です。{: note}
