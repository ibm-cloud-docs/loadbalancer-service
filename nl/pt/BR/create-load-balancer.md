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

# Criar um IBM Cloud Load Balancer
Para criar um serviço IBM Cloud Load Balancer, execute o procedimento a seguir:

1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com/){: new_window} e efetue login em sua conta.

2. Clique em **Catálogo** e, em seguida, na seção Infraestrutura, navegue para **Rede > Balanceadores de carga**.

	<img src="images/catalog-load-balancer.png" alt="drawing" style="width: 600px;"/>

3. Selecione o **IBM Cloud Load Balancer** (seleção padrão) e clique em **Criar**. 

	Se você vir **Upgrade**, em vez de **Criar**, será necessário vincular sua conta do IBM Cloud Infrastructure (Softlayer) seguindo [estas etapas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/account/softlayerlink.html#link_customer_accounts)

	<img src="images/create-load-balancer.png" alt="drawing" style="width: 600px;"/>

4. Selecione seu data center preferencial no menu suspenso **Data center**, revise as informações e, em seguida, clique em **Avançar**.

	<img src="images/select-datacenter.png" alt="drawing" style="width: 600px;"/>

5. Especifique seu tipo de balanceador de carga.

	Para aplicativos voltados à Internet que precisam de acesso à Internet pública, selecione **Pública (voltado à Internet)**.

	<img src="images/select-lb-type.png" alt="drawing" style="width: 600px;"/>
	
	Por padrão, o balanceador de carga Público recebe um endereço IP público exclusivo globalmente do conjunto de endereços globais da IBM. Se, no entanto, você desejar designar a ele endereços públicos de seu próprio conjunto de endereços ou desejar implementá-lo protegido por um serviço de firewall dentro de sua conta, verifique se a sua sub-rede pública tem [endereços IP suficientes](troubleshooting-provisioning.html) e selecione **Alocar de uma sub-rede pública em sua conta**.

	Para aplicativos internos apenas que não precisam de acesso à Internet pública, escolha o tipo **Interno (Privado)**.

	<img src="images/lb-type-private.png" alt="drawing" style="width: 500px;"/>

	Para os tipos de balanceador de carga voltados à Internet e internos, selecione uma das sub-redes privadas dentro da conta que você deseja implementar seu balanceador de carga. Os servidores de aplicativos devem estar acessíveis nessa sub-rede. Se necessário, ative o VLAN Spanning para assegurar a conectividade de rede apropriada.

	Caso não veja nenhuma sub-rede privada, clique em **Anterior** e, em seguida, selecione um data center diferente com sub-redes privadas.

6. Clique em **Avançar** para concluir a configuração.

## O que vem a seguir
Configure o Load Balancer com os [parâmetros básicos](begin-lb-config.html).
