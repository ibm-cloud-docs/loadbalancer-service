---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

keywords: load balancer, compare, explore

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
{:row-headers .row-headers}

# IBM ロード・バランサーの探索
{: #explore}

IBM© Cloud では複数のロード・バランシング・ソリューションを提供しており、その中から選択することになります。 次の表は、ロード・バランシング・ソリューションを比較したもので、適切なソリューションの選択に役立ちます。 個々のオファリングの詳細については、表の中のそれぞれのオファリングの名前をクリックしてください。

右にスクロールすると、表の残りの部分が表示されます。
{: important}


|        | [{{site.data.keyword.loadbalancer_full}}](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)| [Local Load Balancer](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (共有)| [Local Load Balancer](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (専用)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (標準)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (プラチナ) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**パブリック VIP**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**プライベート VIP**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)||![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**Layer 4 LB**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**Layer 7 LB**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|Cookie パーシスタンス|Cookie パーシスタンス|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**ヘルス・チェック**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**水平スケーリング**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|||| |
|**SSL オフロード**|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**管理**|IBM ポータルを介して|IBM ポータルを介して|IBM ポータルを介して|自己管理 (ベンダー GUI)|自己管理 (ベンダー GUI) |
|**高可用性**|標準装備|標準装備|オプション|オプション|オプション |
|**拡張 LB (TCP 最適化、圧縮、キャッシング、WAF)**||||制限付き|![チェック・マーク・アイコン](../../icons/checkmark-icon.svg)|
|**グローバル LB (GLB)**|||||![チェック・マーク・アイコン](../../icons/checkmark-icon.svg) |
|**料金**|利用ベース|月額定額|月額定額|月額定額|月額定額 |
{: row-headers}
{: class="comparison-table"}
{: caption="IBM のロード・バランサー・オファリングの比較" caption-side="top"}
{: summary="This table all of IBM's load balancer offerings, and provides links to their documentation."}
