---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Balanceamento de carga da Camada 7
O IBM Cloud Load Balancer Service distribui o tráfego entre várias instâncias do servidor, incluindo instâncias do bare metal e do servidor virtual, usando dados da Camada 7 (camada de aplicativo). 

 * O tráfego de dados a ser distribuído é classificado usando políticas e regras. 
 * As políticas definem a ação a ser tomada quando o tráfego de dados corresponde a todas as regras associadas a uma política.
 * O balanceamento de carga da Camada 7 (L7) é suportado somente para tráfego HTTP e HTTPS.

## Políticas e regras da Camada 7 
Uma política da Camada 7 é associada a uma porta do aplicativo front-end. Várias políticas podem ser associadas a uma porta front-end. 

 * Essas políticas são avaliadas em ordem, com base na prioridade designada a cada política. 
 * Uma ação associada é executada quando a política é correspondida.
 * Cada regra da L7 é associada a uma política. 
 * Se todas as regras associadas à política forem avaliadas como `true`, a política será correspondida, portanto, a ação associada será tomada.

Consulte [Política e regras da L7](l7-policy.html) para obter detalhes adicionais.

## Conjuntos da Camada 7
Cada conjunto de balanceador de carga da Camada 7 contém uma ou mais instâncias de servidor lógico. 

 * Cada instância de servidor lógico é identificada por um endereço IP e um número de porta. 
 * Cada conjunto tem um monitor de funcionamento associado a ele, que monitora o funcionamento de todos os servidores no conjunto.
 * Um conjunto pode ser configurado para persistência de sessão. 
 * Use o endereço IP de origem do cliente para configurar a persistência de sessão.

Consulte [Conjuntos da L7](l7-pool.html) para obter detalhes adicionais.
