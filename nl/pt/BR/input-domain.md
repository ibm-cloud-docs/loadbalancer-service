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

# Inserir informações sobre o seu domínio
Insira informações sobre o domínio que você deseja proteger e para o qual deseja fornecer balanceamento de carga global.

1. Clique em **Visão geral** no lado esquerdo da tela Introdução. Insira seu Nome de domínio (ou Nome do subdomínio) e clique em **Incluir domínio**. 
    
    <img src="images/Reliability3.png" alt="drawing" style="width: 300px;"/>
    
    **NOTA:** o IBM Cloud Internet Service não é um registrar de DNS, portanto, esse domínio (ou subdomínio) deve ter sido criado anteriormente.

    Na seção Detalhes do serviço, você perceberá que o domínio recém-incluído mostrará inicialmente um estado Pendente. 

    <img src="images/Reliability4.png" alt="drawing" style="width: 300px;"/>    

2. Navegue até a página de administração de seu domínio com seu respectivo registro DNS e delegue seu domínio/subdomínio a servidores de nomes IBM definindo registros de NS.

Pode ser necessário esperar até 24 horas para que suas informações sejam replicadas no banco de dados DNS. Assim que estiverem replicadas, seu estado de domínio será mudado para Ativo. 

<img src="images/Reliability5.png" alt="drawing" style="width: 300px;"/>    
