---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Defina o balanceador de carga global

Defina sua configuração do balanceador de carga global especificando um nome de host, incluindo e ajustando seus conjuntos de origem e definindo regras adicionais para controlar como o tráfego é entregue aos clientes.

1. Crie seu Balanceador de carga global, clicando no botão Criar balanceador de carga à direita.  

2. Especifique o nome do host para o seu domínio e ajuste o valor TTL se desejar (o padrão é 60 segundos) e use **Incluir conjunto** para incluir seus Conjuntos de origens. 

   <img src="images/Reliability11.png" alt="drawing" style="width: 300px;"/>
   
   **NOTA:** nomes de host combinados com nomes de domínio formam nomes completos de domínio (FQDN) para seu aplicativo. Seus usuários finais se conectam ao seu aplicativo usando esse FQDN. 
   
3. Ajuste as prioridades relativas de seus conjuntos de origem, clicando nas setas para cima e para baixo à esquerda do conjunto. As solicitações de aplicativo dos usuários finais são entregues em modo round-robin por esses conjuntos de origem. 
   
   <img src="images/Reliability12.png" alt="drawing" style="width: 300px;"/>   
   
4. Opcionalmente, é possível definir regras adicionais para controlar como o tráfego é entregue a clientes de diferentes regiões geográficas. No exemplo abaixo, os clientes que chegam da região sul da América do Sul são roteados para o conjunto de origem da Costa Oeste dos EUA. É possível usar essas regras para direcionar os clientes para sua região mais próxima possível. Se alguma dessas regiões falhar, as solicitações serão roteadas para outros locais em funcionamento disponíveis, para que os usuários finais não sejam afetados pelo tempo de inatividade. 

   <img src="images/Reliability13.png" alt="drawing" style="width: 300px;"/>   
   
5. Clique em **Prover recursos** para concluir a configuração de seu balanceador de carga global. 
6. Por fim, verifique a conectividade com seu aplicativo digitando `FQDN URL` em uma janela do navegador móvel. Você verá uma mensagem de boas-vindas se puder se conectar.
