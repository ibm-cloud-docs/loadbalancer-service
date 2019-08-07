---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policies, rules, pools

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

# Balanceamento de carga da Camada 7
{: #layer-7-load-balancing}

O {{site.data.keyword.loadbalancer_full}} Service distribui o tráfego entre múltiplas instâncias do servidor, incluindo instâncias bare-metal e de servidor virtual, usando dados da Camada 7 (camada de aplicativo).

 * O tráfego de dados a ser distribuído é classificado usando políticas e regras.
 * As políticas definem a ação a ser tomada quando o tráfego de dados corresponde a todas as regras associadas a uma política.
 * O balanceamento de carga da Camada 7 (L7) é suportado somente para tráfego HTTP e HTTPS.

## Políticas e regras da Camada 7
{: #layer-7-policies-and-rules}
Uma política da Camada 7 é associada a uma porta do aplicativo front-end. Várias políticas podem ser associadas a uma porta front-end.

 * Essas políticas são avaliadas em ordem, com base na prioridade designada a cada política.
 * Uma ação associada é executada quando a política é correspondida.
 * Cada regra da L7 é associada a uma política.
 * Se todas as regras associadas à política forem avaliadas como `true`, a política será correspondida, portanto, a ação associada será tomada.

Consulte [Política e regras da L7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy) para obter detalhes adicionais.

## Conjuntos da Camada 7
{: #layer-7-pools}
Cada conjunto de balanceador de carga da Camada 7 contém uma ou mais instâncias de servidor lógico.

 * Cada instância de servidor lógico é identificada por um endereço IP e um número de porta.
 * Cada conjunto tem um monitor de funcionamento associado a ele, que monitora o funcionamento de todos os servidores no conjunto.
 * Um conjunto pode ser configurado para persistência de sessão.
 * Use o endereço IP de origem do cliente para configurar a persistência de sessão.

Consulte [Conjuntos da L7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool) para obter detalhes adicionais.
