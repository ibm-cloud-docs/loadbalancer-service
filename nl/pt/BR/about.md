---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: about, load balancer, overview, features

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

# Sobre o {{site.data.keyword.loadbalancer_full}}
{: #about-ibm-cloud-load-balancer}

O serviço {{site.data.keyword.loadbalancer_full}} ajuda os clientes a melhorar a disponibilidade de seus
aplicativos críticos aos negócios, distribuindo o tráfego entre múltiplas instâncias do servidor
de aplicativos e encaminhando o tráfego somente para instâncias em funcionamento.

## Visão geral de recursos
{: #overview-of-features}

O {{site.data.keyword.loadbalancer_full}} Service oferece os recursos a seguir:

* Balanceador de carga público (voltado para a Internet)
	* Serviço publicamente acessível por meio de seu nome completo do domínio (FQDN)
	* Instâncias do servidor de backend em sub-redes privadas
* Balanceador de carga interno
	* Serviço acessível de modo privado por meio de seu nome completo do domínio (FQDN)
	* As solicitações do cliente são roteadas por meio da rede privada
	* Instâncias do servidor de backend em sub-redes privadas
* Balanceamento de carga básico
	* Distribuição de tráfego com base nas informações da porta do aplicativo Layer-4
	* Suporte para aplicativos baseados em HTTP, HTTPS e TCP
	* Variedade de métodos de balanceamento de carga, como round-robin (RR), round-robin ponderado e menos conexões
	* Balanceamento de carga entre servidor virtual e instâncias de cálculo bare metal que residem localmente em um data center
* Verificações de funcionamento do servidor
	* Monitoramento periódico de funcionamento do servidor para assegurar que o tráfego seja encaminhado apenas para servidores funcionais
	* Verificações de funcionamento de Layer-4 para portas TCP e verificações de funcionamento de Layer-7 para porta HTTP
* Transferência de SSL
	* Encerramento de tráfego SSL (HTTPS) recebido usando comunicação HTTP de texto sem formatação com servidores de backend
* Gerenciamento de tráfego avançado
	* Permanência do cliente (persistência de sessão)
	* Máximo de conexões por porta virtual
* Fácil gerenciamento usando a interface gráfica intuitiva e a API
* Confiabilidade integrada
* Definição de preço por utilização
* Monitoramento
    * Monitora as métricas de Rendimento, Conexões ativas e Taxa de conexão para protocolos HTTP, HTTPS e TCP sobre intervalos de tempo especificados pelo usuário. Consulte [Monitorando métricas](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer) para obter detalhes adicionais.
* Suporte da Camada 7
    * O tráfego HTTP/HTTPS é roteado para diferentes serviços de backend com base no cabeçalho de HTTP e é feito usando políticas e regras. As regras são usadas para classificar o tráfego e se baseiam nos campos de cabeçalho de HTTP. Quando o tráfego corresponde a todas as regras, uma ação especificada pela política é executada.
* Suporte para região multizona (MZR)
    * Os nós balanceadores de carga são instanciados em diferentes data centers de uma MZR. Consulte [Visão geral da região multizona](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview) para obter mais informações.
* Logs de dados
    * Com os logs de dados ativados, os logs do balanceador de carga serão encaminhados para
o [IBM Cloud Log Analysis Service ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}. Os clientes podem visualizar seus logs de dados usando o [IBM Cloud Log Analysis Service ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}.
