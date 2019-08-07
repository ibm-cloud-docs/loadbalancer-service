---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: health check, http, tcp, ports

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

# Executando verificações de funcionamento com o {{site.data.keyword.loadbalancer_full}}
{: #performing-health-checks-with-ibm-cloud-load-balancer}

As definições de verificação de funcionamento são obrigatórias para cada uma das portas do aplicativo back-end. A porta e o protocolo na configuração de verificação de funcionamento deverão corresponder à porta e ao protocolo de back-end definidos, caso contrário, a configuração será rejeitada.

O balanceador de carga realiza verificações de funcionamento periódicas para monitorar o funcionamento das portas back-end e encaminha o tráfego do cliente para elas adequadamente. Se uma determinada porta do servidor de back-end for encontrada inoperante, nenhuma nova conexão será encaminhada para ela. O balanceador de carga continuará monitorando o funcionamento dessas portas inoperantes e continuará seu uso se novamente se tornarem funcionais passando com sucesso por duas tentativas de verificação de funcionamento consecutivas.

As verificações de funcionamento com relação às portas HTTP/HTTPS e TCP são realizadas conforme a seguir:

* **HTTP:** uma solicitação de `HTTP GET` em uma URL pré-especificada é enviada para a porta do servidor de back-end. A porta do servidor é marcada como funcional ao receber uma resposta `200 OK`. A URL `GET` padrão é "/" por meio da GUI e pode ser customizada.

* **HTTPS:** aplicável somente quando a criptografia de back-end está ativada e o protocolo de back-end está configurado como HTTPS. O mecanismo é o mesmo que o do **HTTP**, exceto que todas as mensagens de verificação de funcionamento são criptografadas por SSL. Para obter mais informações sobre criptografia de back-end, consulte /docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-setting-setting-backend-encryption

* **TCP:** o Load Balancer tenta abrir uma conexão TCP com o servidor de back-end em uma porta TCP especificada. A porta do servidor será marcada como funcional se a tentativa de conexão for bem-sucedida e a conexão será então encerrada.

	O intervalo de verificação de funcionamento padrão é de cinco segundos, o tempo limite padrão com
relação a uma solicitação de verificação de funcionamento é de dois segundos e o número padrão de
novas tentativas é de dois.
  {: note}
