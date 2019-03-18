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
{:faq: data-hd-content-type='faq'}

# Perguntas frequentes do IBM Cloud Load Balancer
{: #faqs-for-ibm-cloud-load-balancer}

Esta seção contém respostas para algumas das perguntas mais frequentes sobre o IBM© Cloud Load Balancer Service.

## Quantas opções de balanceamento de carga estão disponíveis no {{site.data.keyword.BluSoftlayer_notm}}?
{:faq}

Para uma comparação detalhada de ofertas IBM Load Balancer, consulte [Explorar Load Balancers](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-explore).

## Posso usar um nome DNS diferente para meu balanceador de carga?
{:faq}

Embora o nome DNS designado automaticamente para o balanceador de carga não seja customizável, é possível incluir um registro CNAME (Nome Canônico) que aponta seu nome DNS preferencial para o nome DNS do balanceador de carga designado automaticamente. 

Por exemplo, se o número de sua conta for 123456, o balanceador de carga será implementado no data center `dal09` e seu nome será `myapp`, o nome DNS do balanceador de carga designado automaticamente será `myapp-123456-dal09.lb.bluemix.net`. Seu nome DNS preferencial é `www.myapp.com`. É possível incluir um registro CNAME (por meio do provedor DNS usado para gerenciar myapp.com) apontando `www.myapp.com` para o nome DNS do balanceador de carga myapp-12345-dal09.lb.bluemix.net`.

## Qual é o número máximo de portas virtuais que podem ser definidas com o meu serviço de balanceador de carga?
{:faq}

Ao tentar criar um novo serviço de balanceador de carga, será possível definir até duas portas virtuais. É possível definir portas virtuais adicionais após a criação do serviço. O número máximo de portas virtuais permitidas é 10.

## Qual é o número máximo de instâncias de cálculo que podem ser associadas ao balanceador de carga?
{:faq}

50.

## Minhas instâncias de cálculo de backend podem ficar em uma sub-rede diferente da sub-rede do balanceador de carga?
{:faq}

Sim, o balanceador de carga e as instâncias de cálculo conectadas a ele podem ficar em sub-redes diferentes, mas o **VLAN Spanning** precisa ser ativado para que o balanceador de carga se comunique e encaminhe solicitações para a instância de cálculo. Consulte [Resolução de problemas do VLAN Spanning](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-vlan-spanning-troubleshooting) para obter mais informações.

## Quais são as configurações padrão e os valores permitidos para os vários parâmetros de verificação de funcionamento?
{:faq}

As configurações padrão e os valores permitidos são listados abaixo:

* **Intervalo de verificação de funcionamento:** o padrão é 5 segundos, o intervalo é de 2 a 60 segundos
* **Tempo limite de resposta de verificação de funcionamento:** o padrão é 2 segundos, o intervalo é de 1 a 59 segundos
* **Máximo de novas tentativas:** o padrão é 2 novas tentativas e o intervalo é de 1 a 10 novas tentativas

**NOTA:** o valor de tempo limite de resposta de verificação de funcionamento deve sempre ser menor que o valor do intervalo de verificação de funcionamento.

## Posso usar instâncias de cálculo que residam em data centers remotos com esse serviço?
{:faq}

Recomendamos que seu serviço de balanceador de carga e suas instâncias de cálculo residam localmente dentro do mesmo data center. A interface gráfica (GUI) do serviço de balanceador de carga não mostrará as instâncias de cálculo de outros data centers remotos. Entretanto, a GUI incluirá instâncias de cálculo de outros data centers dentro da mesma cidade (por exemplo, data centers cujos nomes compartilham as três primeiras letras, como DALxx). É possível usar a interface da API para incluir instâncias de cálculo de qualquer data center remoto.

## Qual versão do TLS é suportada com transferência de SSL?
{:faq}

O Cloud Load Balancer Service suporta o TLS 1.2 com finalização de SSL.

A lista a seguir detalha as cifras suportadas (listadas em ordem de precedência):  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## Qual é o número máximo de instâncias do serviço Load Balancer que posso criar dentro de minha conta?
{:faq}

Atualmente, é possível criar até 50 instâncias de serviço. Se você precisar de mais instâncias, entre em contato com o Suporte IBM. 

## O serviço IBM Cloud Load Balancer pode ser usado com o VMWare?
{:faq}

As máquinas virtuais VMWare designadas a endereços privados móveis do SoftLayer podem ser especificadas como servidores de backend para o balanceador de carga. Esse recurso está atualmente disponível apenas usando a API e não a IU da web (GUI). Os IPs privados móveis incluídos usando a API aparecem como "Desconhecido" na GUI, uma vez que eles não são designados pelo SoftLayer. Observe que esse tipo de configuração pode ser usado com outros hypervisors, como Xen e KVM também.

As máquinas virtuais VMWare designadas a endereços não do SoftLayer (como redes VMWare NSX) não podem ser incluídas diretamente como servidores de backend no balanceador de carga. Entretanto, dependendo de sua configuração, talvez seja possível configurar um intermediário, como um gateway NSX, que tenha um endereço privado do SoftLayer como o servidor de backend para o balanceador de carga (com os servidores reais sendo VMs conectados à(s) rede(s) gerenciada(s) pelo VMware NSX).

## Se eu optar por usar uma VLAN pública sob minha conta para implementar meu balanceador de carga e tiver um firewall implementado em minha VLAN pública, quais configurações serão necessárias em meu firewall para trabalhar com meu serviço de balanceador de carga?
{:faq}

A porta TCP 56501 é usada para gerenciamento. Assegure-se de que o tráfego para essa porta e as portas do seu aplicativo não sejam bloqueados por seu firewall, caso contrário, o fornecimento do balanceador de carga falhará.

## E se eu não puder ver as métricas de monitoramento de um Load Balancer existente depois de vincular minha conta do Softlayer ao IBM Cloud? 
{:faq}

As métricas de monitoramento não ficarão disponíveis para os balanceadores de carga existentes após a vinculação das contas. Deve-se recriar os balanceadores de carga ou o suporte de contato. Métricas de monitoramento para balanceadores de carga recém-criados ficarão disponíveis.

## Os endereços IP do balanceador de carga são corrigidos?
{:faq}

Não é possível garantir que os endereços IP do balanceador de carga permaneçam constantes devido à elasticidade incorporada ao serviço. Conforme a capacidade aumentar para cima ou para baixo, você verá mudanças nos IPs disponíveis associados ao FQDN de sua instância.

**NOTA:** é necessário usar o FQDN, e não endereços IP em cache.

## Se eu tiver um firewall implementado em minha VLAN privada, quais configurações serão necessárias para que ele funcione com meu serviço de balanceador de carga?
{:faq}

Consulte o tópico [Intervalos de IP do IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges) para obter informações sobre como permitir intervalos de IP por meio do firewall.

## Por que não posso ver a configuração da Camada 7 na IU?
{:faq}

Atualmente, o suporte da Camada 7 fica disponível apenas por meio de APIs públicas, mas essa funcionalidade estará disponível na IU em breve. Consulte a seção Camada 7 da [Documentação das APIs](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-api-reference) para obter mais informações.

## Quais informações eu preciso para arquivar um chamado de suporte?
{:faq}

Para arquivar um chamado de suporte, forneça o nome do produto ("IBM Cloud Load Balancer"), o UUID de seu balanceador de carga (se possível) e o número da conta do Softlayer. O UUID pode ser localizado na URL depois de navegar para a página de visão geral do balanceador de carga fornecido.
