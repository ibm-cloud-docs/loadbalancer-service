---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: ssl, offload, cipher, suite

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

# Transferência SSL com o IBM Cloud Load Balancer
{: #ssl-offload-with-ibm-cloud-load-balancer}

Para todas as conexões HTTPS recebidas, o serviço de balanceador de carga finaliza a conexão SSL e estabelece uma comunicação HTTP de texto sem formatação com o servidor de back-end. As tarefas de handshakes SSL intensivas de CPU e as tarefas de criptografia/decriptografia são deslocadas dos servidores de back-end, permitindo que eles usem todos os seus ciclos de CPU para processar o tráfego de aplicativos.

É necessário um certificado SSL para que o balanceador de carga execute tarefas de transferência de SSL. É possível usar um certificado SSL pré-existente ou comprar um novo certificado e gerenciá-lo por meio
do [IBM© Cloud Certificate Store ![Ícone de linkexterno](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}.


## Conjuntos de cifras SSL
{: #ssl-cipher-suites}

O serviço do balanceador de carga suporta o TLS versão 1.2 com a transferência de SSL.

As cifras SSL a seguir são suportadas por seu balanceador de carga:

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

Se o balanceador de carga tiver uma ou mais portas de aplicativo de front-end HTTPS (protocolos) configuradas, por padrão, todas as cifras SSL predefinidas acima serão ativadas para o balanceador de carga.

Se necessário, será possível optar por ativar cifras SSL diferentes para seu balanceador de carga. Para obter informações adicionais, consulte [Escolher um conjunto de cifras preferenciais para seu aplicativo HTTPS](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
{: note}
