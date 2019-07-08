---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# Registro de Dados
{: #data-logging}

Os logs de dados e de verificação de funcionamento são valiosos para propósitos de depuração
e manutenção. Com o recurso de criação de log ativado, o IBM Load Balancer encaminhará esses logos para o [IBM Cloud Log Analysis Service ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://logging.ng.bluemix.net){:new_window} em sua conta.

É possível ativar ou desativar esse recurso:

* Criando um novo balanceador de carga e configurando esse recurso como ativado.
* Usando a API `enableOrDisableDataLogs`.

## Visualizando logs no IBM Cloud Logging Analysis Service
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

Efetue login no [IBM Cloud Logging Analysis Service ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://logging.ng.bluemix.net){:new_window} com a conta do IBM Cloud do cliente. Os logs podem ser visualizados no Kibana. Consulte [esse tópico](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana) para obter mais informações.

Os logs de dados serão enviados somente se as contas do Softlayer e do IBM Cloud
estiverem vinculadas. Selecione a conta do IBM Cloud associada à sua conta do Softlayer e,
em seguida, efetue login no painel do Kibana.
{: tip}

## Exemplos de saída de log
{: #log-output-examples}

A saída a seguir é um exemplo de um log de dados do IBM Cloud Load Balancer:

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` é o nome do balanceador de carga
e `dal09` é o data center.
* `323698` é o ID da conta. `643866` é o ID do balanceador de carga. `713576` é o ID do membro.
* `xxx.xxx.xxx.xxx` é um IP público que foi mascarado para GDPR.

A saída a seguir é um exemplo de um log de verificação de funcionamento dentro do IBM Cloud Logging Analysis Service:

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` é o endereço IP do membro.
* `682175` é o ID do membro.
