---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: traffic, management, connection, persistence

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

# Gerenciamento avançado de tráfego com o {{site.data.keyword.loadbalancer_full}}
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

Esta seção discute diversos recursos avançados de gerenciamento de tráfego disponíveis
com o serviço {{site.data.keyword.loadbalancer_full}}.

## Máximo de conexões
{: #max-connections}

Use a configuração 'máximo de conexões' para limitar o número máximo de conexões simultâneas em uma determinada porta virtual de front-end. Por padrão, nenhum limite é especificado. O máximo de conexões simultâneas possíveis em uma determinada porta virtual de front-end ou do sistema em todas as portas virtuais de front-end é 15.000.  

## Persistência de sessão
{: #session-persistence}

O balanceador de carga suporta persistência de sessão com relação às portas VIP fornecidas
com base no `source IP` da conexão. Como exemplo, se a persistência de sessão estiver ativada para a porta 80 (HTTP), as tentativas de conexão HTTP subsequentes do mesmo cliente (mesmo IP de origem) serão persistentes no mesmo servidor de back-end. Esse recurso está disponível para os três protocolos suportados (HTTP, HTTPS e TCP).

O balanceador de carga suporta um máximo de 10.000 entradas de persistência do cliente. O prazo de expiração dessas entradas é 10 minutos. As solicitações adicionais recebidas do mesmo cliente depois de 10 minutos podem ser encaminhadas para um servidor de back-end diferente. Se a entrada de persistência de sessão não tiver expirado, mas a porta back-end tiver se tornado inoperante, um novo servidor será selecionado para encaminhar quaisquer conexões subsequentes do cliente.  

## Keep alive HTTP
{: #http-keep-alive}
O balanceador de carga suporta `Keep alive HTTP`, contanto que esteja ativado no cliente e nos servidores de back-end. O balanceador de carga tenta reutilizar as conexões HTTP do lado do servidor para aumentar a eficiência da conexão e reduzir a latência.

## Tempos limite de conexão
{: #connection-timeouts}
Os valores de tempo limite a seguir são usados pelo balanceador de carga. Esses valores não podem ser customizados neste momento.

| Nome | Descrição | Tempo limite |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
| Tentativa de conexão do lado do servidor    | O espaço de tempo máximo que o balanceador de carga pode usar para estabelecer conexão TCP com o servidor de backend. Se a tentativa de conexão for malsucedida, o balanceador de carga tentará o próximo servidor disponível, de acordo com o método de balanceamento de carga que tiver sido configurado. | 5 segundos   |
| Conexão inativa do lado do cliente  | O tempo inativo máximo, após o qual o balanceador de carga desativará a conexão do lado do cliente, no caso de o cliente não ter conseguido fechar sua conexão corretamente.| 50 segundos  |
| Conexão inativa do lado do servidor | O tempo inativo máximo (com a configuração do protocolo de backend de TCP), após o qual o balanceador de carga fechará a conexão do lado do servidor. Com a configuração do protocolo de backend de HTTP, se o balanceador de carga falhar ao receber uma resposta à sua solicitação de HTTP dentro da janela de tempo limite inativo, ele retornará uma mensagem de erro para o cliente de término.                                | 50 segundos |
{: caption="Tabela 1. Valores de tempo limite do balanceador de carga" caption-side="top"}

## Preservando o endereço IP do cliente de término
{: #preserving-end-client-ip-address}

O balanceador de carga funciona como um proxy reverso, que finaliza o tráfego recebido do cliente. Ele estabelece uma conexão separada com a instância do servidor de back-end, usando seu próprio endereço IP. Para conexões HTTP com os servidores de backend (em conexões HTTP ou HTTPS de front-end), o balanceador de carga preserva o endereço IP do cliente original, incluindo-o dentro do cabeçalho `X-Forwarded-For HTTP`. Para conexões TCP, as informações de IP do cliente original não são preservadas.
