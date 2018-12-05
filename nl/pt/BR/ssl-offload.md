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

# Transferência de SSL

Para todas as conexões HTTPS recebidas, o serviço de balanceador de carga finaliza a conexão SSL e estabelece uma comunicação HTTP de texto sem formatação com o servidor de back-end. As tarefas de handshakes SSL intensivas de CPU e as tarefas de criptografia/decriptografia são deslocadas dos servidores de back-end, permitindo que eles usem todos os seus ciclos de CPU para processar o tráfego de aplicativos. 

É necessário um certificado SSL para que o balanceador de carga execute tarefas de transferência de SSL. É possível usar um certificado SSL preexistente ou comprar um novo e gerenciá-lo por meio do [IBM Cloud Certificate Store](https://control.softlayer.com/security/sslcerts). 

# Conjuntos de cifras SSL
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

**NOTA:** será possível optar por ativar cifras diferentes de SSL para seu balanceador de carga, se necessário. Para obter informações adicionais, consulte [Escolher um conjunto de cifras preferenciais para seu aplicativo HTTPS](custom-ciphers.html).
