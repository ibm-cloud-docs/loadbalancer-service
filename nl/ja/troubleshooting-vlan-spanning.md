---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: vlan, troubleshooting, problems, questions

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

# ロード・バランサー VLAN スパンニングに関するトラブルシューティング
{: #load-balancer-vlan-spanning-troubleshooting}

このトピックでは、ロード・バランサーと、ロード・バランサーに接続されたコンピュート・インスタンスが別々のサブネットにある場合に発生する可能性のある一般的な問題について説明します。 ロード・バランサーが、異なるサブネットにあるコンピュート・インスタンスと通信して要求を転送するためには、VLAN スパンニングが有効にされている必要があります。

1. [カスタマー・ポータル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://control.softlayer.com){:new_window} にログインし、**「ネットワーク」 > 「IP 管理」**と進み、**「VLAN」**をクリックします。

2. **「VLAN スパンニング」**を**「オン」**に切り替えます。

<img src="images/vlan-spanning.png" alt="描画" style="width: 500px;"/>

こうすることによって、ロード・バランサーとコンピュート・インスタンス間の通信が開きます。
