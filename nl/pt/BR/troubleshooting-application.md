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

# Resolução de problemas do servidor de aplicativos
{: #application-server-troubleshooting}

Este tópico fornece informações sobre problemas comuns que podem ser encontrados ao usar o balanceador de carga.

## O servidor de back-end está inoperante
Se o funcionamento do servidor de back-end estiver falhando, tente verificar a lista a seguir para testar e corrigi-lo:

* A porta do protocolo de back-end configurado corresponde à porta em que seu aplicativo está atendendo?
* A verificação de funcionamento configurada tem as informações corretas de protocolo (TCP ou HTTP), porta e URL (para HTTP)? Para HTTP, assegure-se de que seu aplicativo responda com `200 OK` para a URL de verificação de funcionamento configurada.
* O servidor de back-end está em uma sub-rede diferente do balanceador de carga? Se não estiver, assegure-se de que o VLAN Spanning esteja ativado.
* O servidor de back-end é um servidor virtual com um grupo de segurança ativado? Se for, assegure-se de que as regras do grupo de segurança permitam o tráfego entre o balanceador de carga e o servidor virtual.
