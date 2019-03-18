---

copyright:
  years: 2017, 2018
lastupdated: "2019-02-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Atualizações recentes do IBM Cloud Load Balancer
{: #recent-updates-for-ibm-cloud-load-balancer}

Descubra sobre novos recursos atualizados no IBM© Cloud Load Balancer.

## Dezembro de 2018
### Criptografia de back-end e encaminhamento de log de dados
O IBM Cloud Load Balancer agora suporta criptografia de back-end e a capacidade de encaminhar
seus logs de dados. A criptografia de back-end permite a criptografia de tráfego de dados de ponta
a ponta, incluindo o tráfego entre o balanceador de carga e os servidores de back-end. O encaminhamento
de log de dados permite que você envie logs de dados de seus balanceadores de carga para o IBM Bluemix
Log Analysis Service.

## Agosto de 2018
### Suporte da Camada 7
O IBM Cloud Load Balancer agora suporta o balanceamento de carga da Camada 7. Com o suporte da Camada 7 (L7), o tráfego pode ser redirecionado para uma URL, rejeitado ou distribuído para membros do conjunto L7, incluindo as instâncias do bare metal e do servidor virtual. O tráfego de dados recebidos é classificado usando as políticas e as regras da Camada 7. As políticas definem qual ação deve ser tomada quando o tráfego de dados corresponde às regras associadas a elas.

Consulte [Balanceamento de carga da Camada 7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing) para obter detalhes adicionais.

## Abril de 2018
### Escala horizontal
O IBM Cloud Load Balancer agora aumenta a capacidade automaticamente quando sua carga aumenta e reduz a capacidade à medida que ela diminui. Ao criar um balanceador de carga, ele começa com dois dispositivos, mas o número de dispositivos pode ser aumentado para 16 (a partir desta composição), pois o sistema de monitoramento detecta um aumento na carga. Os endereços IP de cada um dos dispositivos ativos são incluídos como DNS A-Records para o Nome completo do domínio (FQDN) do balanceador de carga.

### Balanceador de carga interno
Uma versão "interna" altamente demandada do IBM Cloud Load Balancer está agora disponível. Esse balanceador de carga não é exposto publicamente, mas ainda pode ser usado para balancear aplicativos em suas redes privadas do IBM Cloud (em uma implementação com multicamadas, por exemplo, conforme mostrado na figura).

![Load Balancer interno](./images/InternalLB.png)

Ele é seguro e consistente com as versões anteriores do IBM Cloud Load Balancer no lado público.

### Monitorando métricas
Agora é possível alavancar o serviço "IBM Cloud Monitoring" para monitorar as métricas de desempenho a seguir associadas ao balanceador de carga e ao aplicativo:

* Rendimento
* Taxa de conexão
* Conexões ativas

![Monitorando métricas](./images/Metrics.png)

Até duas semanas de amostras são coletadas e exibidas pela IU da web do balanceador de carga. Os dados também podem ser visualizados no portal de serviço IBM Cloud Monitoring. Se você precisar de dados por mais de duas semanas, dependendo do volume de outras métricas de nuvem que estiver enviando para a sua instância do Cloud Monitoring, talvez seja necessário fazer upgrade de seu plano de monitoramento. Consulte [Métricas de monitoramento](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer) para obter detalhes adicionais

Esse recurso requer que suas contas do IBM Cloud IaaS e PaaS sejam vinculadas, com algumas [etapas simples](/docs/account?topic=account-unifyingaccounts).

### Customização do conjunto de cifras
Agora é possível customizar os conjuntos de cifras usados quando o balanceador de carga está configurado para finalização de SSL.

Ao ativar a finalização de SSL no IBM Cloud Load Balancer (selecionando **HTTPS** como o protocolo de front-end), um conjunto padrão de conjuntos de cifras selecionado cuidadosamente é ativado e está em conformidade com as boas práticas de segurança. A IBM acompanha de perto quaisquer novas vulnerabilidades que possam ser descobertas e atualiza a lista adequadamente. Isso, junto às atualizações contínuas de segurança de componentes de software e hardware, ajuda a manter seus aplicativos sempre seguros.

Consulte [Conjunto de cifras customizado](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application) para obter detalhes adicionais.
