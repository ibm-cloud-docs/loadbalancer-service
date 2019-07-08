---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, pool, http

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# レイヤー 7 プール
{: #layer-7-pool}

レイヤー 7 (L7) プールは、着信要求を処理するためのサーバー (メンバー) の論理グループです。

レイヤー 7 ロード・バランシング機能は、ポリシーおよびルールに基づいて、着信トラフィックを異なるバックエンド・プールに転送できます。この機能は、1 つのロード・バランサーに複数の L7 プールを関連付けることによってサポートされます。 レイヤー 7 プールは、アクションが `redirect to pool` であるレイヤー 7 ポリシーと共に使用されます。

L7 プールは、バックエンド・プロトコルとして HTTP のみをサポートします。

## セッション・パーシスタンス
{: #session-persistence}

レイヤー 7 プールごとにセッション・パーシスタンスを構成することができます。 詳しくは、  
[高度なトラフィック管理](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer)セクションを参照してください。

## レイヤー 7 メンバー
{: #layer-7-members}

レイヤー 7 プールと関連付けられたバックエンド・サーバーはレイヤー 7 メンバーと呼ばれます。

同じバックエンド・サーバーを、毎回異なるポート番号を指定することによって、L7 プールに複数回追加することができます。

## ヘルス・チェックの構成
{: #configure-health-checks}
レイヤー 7 プールごとにヘルス・チェック定義が必須です。 L7 プール用のデフォルトのヘルス・チェックがシステムによって事前設定されます。

アプリケーションのニーズに合うように以下の設定をカスタマイズできます。

 * **間隔 (Interval)**: 2 つの連続するヘルス・チェック試行の間隔 (秒単位)
 * **タイムアウト (Timeout)**: ヘルス・チェック要求に対してシステムが応答を待機する最大時間
 * **最大試行回数 (MaxRetries)**: ポートが正常でないと宣言する前にシステムが行う追加のヘルス・チェック試行の最大回数
 * **URL パス (UrlPath)**: レイヤー 7 ヘルス・チェックの HTTP URL パス。
