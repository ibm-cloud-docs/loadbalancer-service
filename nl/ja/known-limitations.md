---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: limitations, problems, troubleshooting

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

# {{site.data.keyword.loadbalancer_full}} の既知の問題と制限
{: #known-issues-and-limitations-with-ibm-cloud-load-balancer}

このトピックでは、{{site.data.keyword.loadbalancer_full}} サービスの、現時点での既知の問題と制限に関する情報を提供します。

## 既知の問題
{: #known-issues}
現在、{{site.data.keyword.loadbalancer_full}} サービスには以下の問題があります。

* 軽微な問題 - 「サーバー・インスタンス」タブと「プロトコル」タブの**「編集」**ボタンが、すべての項目に適用され、チェック・ボックスを使用して選択された行に制限されない。
* 軽微な問題 - ロード・バランサー・サービスの初期作成中、各種画面を行ったり来たりした場合、カスタム・ヘルス・チェック設定を失う。
* 軽微な問題 - ロード・バランサー・サービスの管理に Internet Explorer 11、Edge、または Safari のブラウザーを使用している時、いくつかの問題が発生する可能性がある。 代わりに、Firefox または Chrome のブラウザーを選択してください。
* 表面的な問題 - 初期サービス作成中、データ・センターのドロップダウン・リストがゆがむ可能性がある。 それでも、希望するデータ・センターを選択できます。
* 表面的な問題 - レビュー・ページの価格情報は十の位に丸められている。 正しい価格は、プラン・ページに表示される価格を参照してください。

## 既知の制限
{: #known-limits}
現在、{{site.data.keyword.loadbalancer_full}} サービスには以下の制限があります。

* 仮想ポート/プロトコルの最大数 - 10
* ロード・バランサーの後ろに配置できるサーバーの最大数 - 50
