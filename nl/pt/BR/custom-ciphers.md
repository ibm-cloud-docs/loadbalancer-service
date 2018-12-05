---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Escolha um conjunto de cifras preferencial para seu aplicativo HTTPS
Algoritmos de cifras que ajudam o IBM Cloud Load Balancer a formar conexões seguras com seus clientes HTTP.

A IBM oferece um conjunto de cifras aprovadas das quais escolher, para que você assegure a comunicação entre o balanceador de carga e seus clientes.

É possível escolher um conjunto de cifras preferencial para um balanceador de carga existente ou designá-lo ao criar um novo. 

## Escolhendo cifras para um balanceador de carga existente
Para escolher uma configuração de conjunto de cifras para um balanceador de carga existente, navegue para a tela do balanceador de carga no portal do cliente e clique na guia Protocolos. Se HTTPS não estiver selecionado como seu protocolo de front-end, você não verá a lista de conjuntos de cifras.

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="drawing" style="width: 700px;"/>
  
Selecione HTTPS para o protocolo de front-end e os Conjuntos de cifras disponíveis serão exibidos em Detalhes do balanceador de carga. 

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="drawing" style="width: 600px;"/>
  
A tabela Cifra é editável e permite selecionar os conjuntos de cifras desejados para o handshake SSL. Clique em **Editar**, selecione as Cifras que deseja implementar e clique em **Salvar**.
  
**NOTA:** para obter uma lista de cifras suportadas, consulte [Transferência de SSL](ssl-offload.html).

## Escolhendo cifras ao criar um novo balanceador de carga

Para escolher o conjunto de cifras ao criar um novo balanceador de carga:

1. Siga as instruções para [criar um balanceador de carga](create-load-balancer.html).
  
2. A configuração do conjunto de cifras é aplicável apenas com o protocolo de front-end HTTPS. Quando você chegar às etapas de configuração da seção **Incluir protocolo**, escolha **Protocolo HTTPS**.

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="drawing" style="width: 500px;"/>
  
3. Um conjunto padrão de cifras já estará selecionado na configuração, mas só será possível editá-lo depois de ter concluído a configuração do balanceador de carga. 
  
	Conclua a configuração do balanceador de carga, seguindo as instruções no tópico. Depois que terminar, será possível ver a lista de cifras padrão na **Guia Protocolos** em **Detalhes do balanceador de carga**.

	<img src="images/View-CustomCiphers.png" alt="drawing" style="width: 600px;"/>
  
4. A tabela Cifra é editável e permite selecionar os conjuntos de cifras desejados para o handshake SSL. Clique em **Editar**, selecione as Cifras que deseja implementar e clique em **Salvar**.
	
	**NOTA:** para obter uma lista de cifras suportadas, consulte [Transferência de SSL](ssl-offload.html).
