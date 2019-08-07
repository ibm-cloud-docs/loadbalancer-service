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

# Explorando balanceadores de carga IBM
{: #explore}

O IBM© Cloud oferece diversas soluções de balanceamento de carga para escolher. A tabela abaixo compara as soluções de balanceamento de carga para ajudá-lo a escolher a mais adequada para você. Para saber mais sobre a oferta individual, clique em seu nome na tabela.

Role para a direita para visualizar o restante da tabela!
{: important}


|        | [{{site.data.keyword.loadbalancer_full}}](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)| [Local Load Balancer](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (Compartilhado)| [Local Load Balancer](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (Dedicado)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (Padrão)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (Platinum) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**VIP Público**|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg) |
|**VIP Privado**|![Ícone de visto](../../icons/checkmark-icon.svg)||![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg) |
|**Camada 4 LB**|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg) |
|**Camada 7 LB**|![Ícone de visto](../../icons/checkmark-icon.svg)|Persistência de Cookie|Persistência de Cookie|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg) |
|**Verificações de funcionamento**|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg) |
|**Escala horizontal**|![Ícone de visto](../../icons/checkmark-icon.svg)|||| |
|**Transferência de SSL**|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg)|![Ícone de visto](../../icons/checkmark-icon.svg) |
|**Gerenciamento**|Por meio do IBM Portal|Por meio do IBM Portal|Por meio do IBM Portal|Autogerenciar (GUI do fornecedor)|Autogerenciar (GUI do fornecedor) |
|**Alta disponibilidade **|Integrado|Integrado|Opcional|Opcional|Opcional |
|**LB Avançado (Otimização de TCP, Compactar, Armazenamento em cache, WAF)**||||Limitado|![Ícone de visto](../../icons/checkmark-icon.svg)|
|**LB Global (GLB)**|||||![Ícone de visto](../../icons/checkmark-icon.svg) |
|**Precificação**|Com base no uso|Simples mensal|Simples mensal|Simples mensal|Simples mensal |
{: row-headers}
{: class="comparison-table"}
{: caption="Uma comparação das ofertas de balanceador de carga da IBM" caption-side="top"}
{: summary="This table all of IBM's load balancer offerings, and provides links to their documentation."}
