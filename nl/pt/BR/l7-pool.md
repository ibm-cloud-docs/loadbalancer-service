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

# Conjunto da Camada 7
{: #layer-7-pool}

Um conjunto da Camada 7 (L7) é um agrupamento lógico dos servidores (membros) para manipulação de solicitações recebidas.

O recurso de balanceamento de carga da Camada 7 pode direcionar o tráfego recebido para diferentes conjuntos de backend com base
nas políticas e regras. Esse recurso é suportado associando vários conjuntos da L7 a um balanceador de carga. Os conjuntos da Camada 7 são usados com as políticas da Camada 7 cuja ação é `redirect to pool`.

Os conjuntos da L7 suportam apenas HTTP como o protocolo de back-end.

## Persistência de sessão
A persistência de sessão pode ser configurada para cada conjunto da Camada 7. Para obter mais detalhes, consulte a  
[seção de tráfego avançado](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Membros da Camada 7

Os servidores de backend associados a um conjunto da Camada 7 são chamados de membros da Camada 7.

O mesmo servidor de backend pode ser incluído várias vezes em conjuntos da L7, especificando sempre um número de porta diferente.

## Configurar verificações de funcionamento
A definição de verificação de funcionamento é obrigatória para cada conjunto da Camada 7. O sistema pré-preenche uma configuração de verificação de funcionamento padrão para conjuntos da L7.

É possível customizar essas configurações para adequar as necessidades do aplicativo:

 * **Intervalo**: o intervalo, em segundos, entre duas tentativas consecutivas de verificação de funcionamento.
 * **Tempo limite**: o período máximo de tempo que o sistema aguardará por uma resposta para a solicitação de verificação de funcionamento.
 * **MaxRetries**: o número máximo de tentativas adicionais de verificação de funcionamento que o sistema fará antes de declarar que o serviço está inoperante.
 * **UrlPath**: o caminho da URL HTTP para a verificação de funcionamento da Camada 7.
