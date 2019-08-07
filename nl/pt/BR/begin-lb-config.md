---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: parameters, load balancing, configure, protocol, health check

subcollection: loadbalancer-service


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Configurando parâmetros do {{site.data.keyword.loadbalancer_full}}
{: #configuring-ibm-cloud-load-balancer-parameters}

Depois de [criar um balanceador de carga](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started), você poderá configurá-lo para balanceamento de carga elástico. Para fazer isso:

1. Nomeie seu balanceador de carga e, opcionalmente, inclua uma descrição.

	<img src="images/lb-config-basic.png" alt="drawing" style="width: 300px;"/>

2. Insira os detalhes de seu perfil de aplicativo identificando os protocolos e as portas em que seu aplicativo está atendendo. É possível usar a mesma configuração para o front-end e o back-end ou expor uma porta front-end diferente (para propósitos de segurança, por exemplo).

3. O método de balanceamento de carga padrão é **Round-robin**. É possível mudá-lo para **Round-robin ponderado** ou **Menos conexões** na lista suspensa, dependendo das necessidades do aplicativo.

4. Opcionalmente, é possível ativar a **Permanência de sessão**. Se ativada, todas as solicitações de um determinado usuário final (por exemplo, um com o mesmo IP de origem) vão para o mesmo servidor de backend para um tempo "permanente" definido pelo sistema.

5. Também é possível configurar o **Limite máximo de conexão** em relação ao aplicativo.

6. Clique em **Incluir protocolo** para especificar portas e protocolos adicionais que seu aplicativo possa estar atendendo. Certifique-se de que todas as portas front-end sejam exclusivas. É possível escolher HTTP, HTTPS ou TCP como seu protocolo de front-end.

	<img src="images/lb-add-protocol.png" alt="drawing" style="width: 300px;"/>

	Um máximo de duas portas pode ser definido no momento da configuração inicial. Portas adicionais poderão ser incluídas posteriormente após a criação da instância de serviço. Consulte [Limitações no número de portas](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-) para obter mais informações sobre o número máximo de portas permitidas.
{:note:}

7. O {{site.data.keyword.loadbalancer_full}} encerra as conexões HTTPS (HTTP sobre SSL) de entrada e
pode se comunicar em HTTP de texto sem formatação com os servidores de aplicativos de back-end
e transfere tarefas SSL com uso intensivo de processador dos servidores se o protocolo de back-end
for selecionado como HTTP. Se o protocolo de back-end selecionado for HTTPS, o tráfego será criptografado
entre o balanceador de carga e os servidores de back-end. Deve-se fazer upload de seu Certificado SSL. Selecione um de seus certificados disponíveis na lista suspensa.  

	<img src="images/lb-ssl-cert.png" alt="drawing" style="width: 300px;"/>

	Se você não tiver um certificado existente, clique em **Incluir um novo certificado**. Isso o leva a um serviço de certificado do IBM Cloud no qual é possível comprar um novo certificado ou fazer upload de um existente.

	Depois de incluir o certificado, retorne para a página Configuração do balanceador de carga e clique no ícone de atualização abaixo da lista suspensa Certificado SSL para visualizar e incluir seu certificado recém-transferido por upload.

	<img src="images/order-ssl-cert.png" alt="drawing" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="drawing" style="width: 300px;"/>

	Nunca exclua qualquer certificado associado aos listeners HTTPS, já que isso pode causar problemas
com a funcionalidade.
  {: note}

8. Clique em **Avançar**.

## Configurar verificações de funcionamento
{: #configure-health-checks}

A definição de verificação de funcionamento é obrigatória para cada uma de suas portas do aplicativo. Essas são as portas back-end identificadas no menu de configuração básica anterior.

<img src="images/config-health-check.png" alt="drawing" style="width: 300px;"/>

O sistema pré-preenche uma configuração de verificação de funcionamento padrão para essas portas back-end. É possível customizar essas configurações para adequar as necessidades do aplicativo.

* **Intervalo**: intervalo em segundos entre duas tentativas de verificação de funcionamento consecutivas
* **Tempo limite**: período máximo de tempo que o sistema aguardará por uma resposta com relação a uma solicitação de verificação de funcionamento
* **Máximo de tentativas**: o número máximo de tentativas de verificação de funcionamento adicionais que o sistema fará antes de declarar que uma porta está inoperante
* **Caminho**: o caminho da URL HTTP para a verificação de funcionamento     

Clique em **Avançar** para ativar sua opção.

## O que vem a seguir
{: #what-s-next}

[Identifique os recursos de seu aplicativo](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources), como conjuntos de origem e mecanismos de verificação de funcionamento.
