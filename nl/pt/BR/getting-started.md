---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# Introdução ao IBM Cloud Load Balancer
{: #getting-started}

Para começar a usar o IBM© Cloud Load Balancer, você precisará de dois itens principais:

* Uma conta com a IBM: [IBMid![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* Um servidor IBM, [Bare Metal](/docs/bare-metal?topic=bare-metal-about) ou [Virtual Server Instance (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

Se precisar de assistência na obtenção de uma conta **IBMid**, entre em contato com seu [representante de vendas IBM![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} para obter orientação adicional.

Se você tiver uma conta existente do IBM Cloud Infrastructure (SoftLayer), será possível [vincular sua conta](/docs/account?topic=account-unifyingaccounts) a seu IBMid.

## Solicitando um balanceador de carga
{: #ordering-a-load-balancer}

Para pedir um serviço do IBM Cloud Load Balancer, selecione **IBM Cloud Load Balancer** no [catálogo do
IBM Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}. Em seguida, clique em Criar e execute o procedimento a seguir:

1. Defina seus parâmetros de serviço básicos, tais como o nome e a descrição.
2. Selecione o seu data center.
3. Selecione um tipo de balanceador de carga de **Público**.
4. Selecione a sub-rede na qual você gostaria implementar seu balanceador de carga.

  A instância do serviço de balanceador de carga terá uma de suas interfaces de rede nesta sub-rede. Assegure-se de que seus servidores de aplicativos estejam nessa sub-rede ou sejam acessíveis nessa sub-rede. Se necessário, ative o VLAN Spanning.
  {: note}

5. Criar protocolos e portas de aplicativo front-end e back-end.

  Para obter mais informações sobre essa configuração, consulte [Configurando parâmetros do IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters).
  {: note}

6. Para ativar a transferência de SSL, configure os protocolos de front-end para
HTTPS e os protocolos de back-end para HTTP. Em seguida, selecione seu Certificado SSL na
caixa suspensa Certificado.

  Todos os certificados SSL existentes são gerenciados por meio do [IBM Cloud Certificate Store  ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}. Se você não tiver um certificado SSL, poderá criar um aqui.

7. Ajuste os parâmetros de verificação de funcionamento, se desejado, caso contrário, use as configurações padrão.

  Para obter mais informações sobre os parâmetros de verificação de funcionamento, consulte [Parâmetros do IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks).
  {: note}

8. Clique em **Anexar servidor** para associar um ou mais instâncias de
servidor atrás do seu balanceador de carga. Você só verá instâncias do servidor locais para seu data center.
9. Revise a página, confirme o Contrato de Prestação de Serviços e, em seguida, clique em **Criar**.

A lista Balanceador de carga é exibida, mostrando todas as suas instâncias de serviço.

Clicar no nome do serviço nessa página o levará para a página de visão geral do serviço. É possível navegar para as guias **Protocolos**, **Verificações de funcionamento** e **Instâncias do servidor** para editar sua configuração posteriormente.

O balanceador de carga recém-criado pode não ser exibido imediatamente nessa lista. Após alguns minutos, o novo balanceador de carga será exibido em uma cor cinza, indicando que o seu status é `Offline`. Depois de mais alguns minutos, o novo balanceador de carga será exibido
em verde, indicando que ele está `Online`. Poderá ser necessário atualizar sua tela
para ver essas mudanças.
{: note}

Consulte [Como usar o IBM Cloud Load Balancer para balanceamento de carga do servidor elástico](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing) para obter orientações passo-a-passo sobre a configuração do seu novo Cloud Load Balancer.
