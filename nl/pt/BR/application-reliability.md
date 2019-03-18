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

# Melhorando a confiabilidade e a escalabilidade do aplicativo com o Balanceamento de carga global do IBM Cloud Internet Services
Se você tiver um website de e-commerce ou estiver hospedando um aplicativo que precise ser acessível a seus usuários finais em todos os momentos, provavelmente você estará preocupado com a disponibilidade 24/7 e com o desempenho de seu aplicativo. 

Os recursos de balanceamento de carga global disponíveis com o IBM Cloud Internet Services (CIS) podem ajudar a melhorar a confiabilidade e a escalabilidade de seus aplicativos, ao mesmo tempo em que oferecem a melhor experiência de usuário final possível. Este guia o acompanha na configuração de balanceamento de carga global.  

## O que você aprenderá

Neste Passo a passo, você aprenderá como configurar uma configuração semelhante à ilustrada abaixo.

<img src="images/Reliability1.png" alt="drawing" style="width: 300px;"/>

Neste exemplo, os recursos do aplicativo são implementados em dois locais de data center, um no oeste dos EUA e outro na costa leste dos EUA. Os usuários finais podem acessar esse aplicativo em todo o mundo. 

Tarefa  | Descrição
------------- | -------------
[Criar uma instância do CIS](create-cis.html) | Comece criando sua instância do IBM Cloud Internet Services (CIS) usando o Portal do cliente
IBM.
[Inserir informações sobre seu domínio](input-domain.html) | Insira informações sobre o domínio que você deseja proteger e para o qual deseja fornecer balanceamento de carga global.
[Iniciar a configuração do Balanceador de carga global](begin-config.html) | Inicie a configuração do Balanceador de carga global.
[Identificar os recursos de aplicativo](identify-app-resources.html) | Identifique os recursos de seu aplicativo, como os conjuntos de origem e os mecanismos de verificação de funcionamento.
[Definir o balanceador de carga global](define-global-lb.html) | Defina a configuração do seu balanceador de carga global, especificando um nome de host, incluindo e ajustando seus conjuntos de origem e definindo regras adicionais para controlar como o tráfego é entregue aos clientes.
