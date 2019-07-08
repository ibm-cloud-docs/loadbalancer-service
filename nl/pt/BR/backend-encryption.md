---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

keywords: encryption, security

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

# Configurando a criptografia de back-end
{: #setting-backend-encryption}

A criptografia de back-end é suportada para permitir a criptografia de tráfego de dados de ponta a ponta. Além do tráfego entre o balanceador de carga e o cliente, o tráfego entre o balanceador de carga e o servidor de back-end também é criptografado.

Para ativar a criptografia de back-end:

* Se você estiver incluindo um novo protocolo HTTPS, configure o front-end e o back-end para **HTTPS**.
* Para protocolos HTTPS existentes, configure o back-end para **HTTPS**.
