---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, provisioning, question, problem

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

# ロード・バランサーのプロビジョンに関するトラブルシューティング
{: #load-balancer-provisioning-troubleshooting}

このトピックでは、IBM© Cloud Load Balancer の新規インスタンスの作成時に発生する可能性のある一般的な問題について説明します。

## サブネットの IP アドレスが不十分
{: #insufficient-ip-addresses-in-your-subnet}

IBM Cloud Load Balancer には、プライベート・サブネットからの 2 つ以上の空き IP アドレスが必要です。 さらに、ロード・バランサーがパブリック・ロード・バランサーであり、かつ、**IBM システム・プール**のオプションが使用されていない場合は、パブリック・サブネットからも 2 つ以上の空き IP アドレスが必要です。

サブネットに空き IP があるかどうかを確認するには、以下のステップを実行します。

1. [カスタマー・ポータル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://control.softlayer.com){:new_window} に移動し、**「ネットワーク」 > 「IP 管理」 > 「サブネット」**と選択して、サブネット・セクションに移動します。

2. 空き IP があるかどうか確認したいサブネットをクリックします。

	<img src="images/subnet_list.png" alt="描画" style="width: 600px;"/>

3. 選択したサブネットの詳細ページに、そのサブネットのすべての IP の状況が表示されます。

## パブリック VLAN およびプライベート VLAN 上のファイアウォールに関する問題
{: #issues-with-firewalls-on-public-and-private-vlans}

ファイアウォール通過の許可対象とする IP 範囲について、[IBM Cloud の IP 範囲](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges)トピックを参照してください。

## ロード・バランサーのエラー・メッセージの表示
{: #viewing-load-balancer-error-messages}

ロード・バランサーのエラー・メッセージを表示するには、以下の手順を実行します。

1. リスト・ページからロード・バランサーをクリックして、ロード・バランサーの詳細を表示します。
2. ロード・バランサーの状況の横にあるエラー記号の上にマウスを置きます。

<img src="images/lbaas_error_message.png" alt="描画" style="width: 500px;"/>

状況が `ERROR` のロード・バランサーを復旧することはできず、そのロード・バランサーは削除する必要があります。
