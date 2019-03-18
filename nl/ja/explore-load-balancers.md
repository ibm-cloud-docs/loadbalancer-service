---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# IBM ロード・バランサーの探索
{: #explore}

IBM© Cloud では複数のロード・バランシング・ソリューションを提供しており、その中から選択することになります。 次の表は、ロード・バランシング・ソリューションを比較したもので、適切なソリューションの選択に役立ちます。 個々のオファリングの詳細については、表の中のそれぞれのオファリングの名前をクリックしてください。 

右にスクロールすると、表の残りの部分が表示されます。


|        | [IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started-with-ibm-cloud-load-balancer)| [Local Load Balancer](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started-with-local-load-balancer#getting-started-with-local-load-balancer) (共有)| [Local Load Balancer](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started-with-local-load-balancer#getting-started-with-local-load-balancer) (専用)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started-with-citrix-netscaler-vpx-software-appliance#getting-started-with-citrix-netscaler-vpx-software-appliance) VPX/MPX (標準)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started-with-citrix-netscaler-vpx-software-appliance#getting-started-with-citrix-netscaler-vpx-software-appliance) VPX/MPX (プラチナ) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**パブリック VIP**|あり|あり|あり|あり|あり |
|**プライベート VIP**|あり|なし|あり|あり|あり |
|**Layer 4 LB**|あり|あり|あり|あり|あり |
|**Layer 7 LB**|あり|Cookie パーシスタンス|Cookie パーシスタンス|あり|あり |
|**ヘルス・チェック**|あり|あり|あり|あり|あり |
|**水平スケーリング**|あり|なし|なし|なし|なし |
|**SSL オフロード**|あり|あり|あり|あり|あり |
|**管理**|IBM ポータルを介して|IBM ポータルを介して|IBM ポータルを介して|自己管理 (ベンダー GUI)|自己管理 (ベンダー GUI) |
|**高可用性**|標準装備|標準装備|オプション|オプション|オプション |
|**拡張 LB (TCP 最適化、圧縮、キャッシング、WAF)**|なし|なし|なし|制限付き|あり |
|**グローバル LB (GLB)**|なし|なし|なし|なし|あり |
|**料金**|利用ベース|月額定額|月額定額|月額定額|月額定額 |
