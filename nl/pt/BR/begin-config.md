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

# Iniciar a configuração do Balanceador de carga global
Inicie a configuração do Balanceador de carga global.

1. Sob a seção **Confiabilidade**, selecione **Balanceador de carga global**. 
    
    <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>

2. Role para baixo até a seção Verificações de funcionamento. 

   **NOTA:** essa configuração é opcional. Se você não definir nenhuma verificação de funcionamento customizada, o sistema usará "/" como o caminho de verificação de funcionamento padrão. 

3. Clique no botão **Criar verificação de funcionamento** para definir uma verificação de funcionamento customizada.   

   Forneça o caminho em que você deseja conduzir as verificações de funcionamento. É possível usar os protocolos HTTP ou HTTPS para suas verificações de funcionamento. 
   
4. Em **Opções avançadas**, é possível customizar outros parâmetros, como o intervalo de verificação de funcionamento, o número de novas tentativas, o método de solicitação e o corpo de resposta, em Opções avançadas. 
   
   <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>
   
5. Clique em **Prover recurso** para concluir a configuração de verificação de funcionamento. 
