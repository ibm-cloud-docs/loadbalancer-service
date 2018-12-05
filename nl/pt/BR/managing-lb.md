---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Monitorando e gerenciando seu serviço
É possível editar sua configuração ou monitorar o desempenho do serviço clicando na URL do nome do serviço na página de resumo do balanceador de carga. 

O **endereço do nome completo do domínio (FQDN)** da instância de serviço do balanceador de carga pode ser visto logo abaixo do nome do serviço. Seus usuários finais poderão se conectar ao aplicativo por meio desse endereço FQDN. Observe que os endereços IP públicos e privados do serviço do balanceador de carga não são expostos ao mundo externo; apenas o endereço FQDN é exposto. 

<img src="images/fqdn-address.png" alt="drawing" style="width: 300px;"/>

A guia **Visão geral** fornece informações de estado de alto nível de seu serviço. Ela exibe o funcionamento atual dos servidores de aplicativos e suas portas. Ela também fornece um resumo rápido do desempenho do sistema - rendimento, taxa de conexão, conexões simultâneas etc. 

Navegue para a guia **Monitoramento** para visualizar os gráficos em tempo real do desempenho do sistema. Esses gráficos podem ser visualizados por porta do aplicativo individual e por várias durações de tempo. 

<img src="images/monitor-lb.png" alt="drawing" style="width: 300px;"/>

É possível editar sua configuração existente navegando para as guias **Protocolos**, **Instâncias do servidor** e **Verificações de funcionamento**. Como exemplo, navegue para a guia Protocolos para definir portas de aplicativo adicionais ou para customizar a lista de cifras SSL. 

<img src="images/protocols-monitor.png" alt="drawing" style="width: 300px;"/>
