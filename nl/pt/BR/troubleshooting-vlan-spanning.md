---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Resolução de problemas do VLAN Spanning do balanceador de carga
Este tópico fornece informações sobre problemas comuns encontrados quando o balanceador de carga e as instâncias de cálculo conectadas ao balanceador de carga estão em sub-redes diferentes. O VLAN Spanning deve ser ativado para que o balanceador de carga se comunique e encaminhe solicitações para calcular instâncias que residem em uma sub-rede diferente.

1. Efetue login no [Portal do cliente](https://control.softlayer.com), navegue para **Rede > Gerenciamento de IP** e, em seguida, clique em **VLANs**.

2. Alterne **VLAN Spanning** para **Ativado**.

<img src="images/vlan-spanning.png" alt="drawing" style="width: 500px;"/>

Isso abre a comunicação entre o balanceador de carga e suas instâncias de cálculo.
