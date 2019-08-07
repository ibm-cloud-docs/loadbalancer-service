---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: basics, load balancing

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

# Executando os fundamentos do {{site.data.keyword.loadbalancer_full}}
{: #performing-ibm-cloud-load-balancer-basics}

O serviço balanceador de carga do IBM© Cloud distribui o tráfego entre múltiplas instâncias do servidor (bare metal e servidor virtual) que residem localmente, no mesmo datacenter.

## Balanceador de carga público
{: #public-load-balancer}

Um nome completo do domínio publicamente acessível é designado para sua instância de serviço do balanceador de carga. Deve-se usar esse nome de domínio para acessar seus aplicativos hospedados atrás do serviço de balanceador de carga. Esse nome de domínio pode ser registrado com um ou mais endereços IP públicos. Os endereços IP públicos e o número de endereços IP públicos podem mudar ao longo do tempo com base nas atividades de manutenção e ajuste de escala, que são transparentes para os usuários finais. As instâncias de cálculo de backend que hospedam seu aplicativo devem estar em uma rede privada do IBM Cloud.

Como boa prática, recomenda-se provisionar os servidores de backend como 'somente privado’, a menos que requeiram conectividade pública direta. Essa prática ajuda a alcançar melhor segurança, além de preservar o endereço IP público. Os aplicativos hospedados nesses servidores de backend continuam acessíveis na rede pública usando o balanceador de carga.
{: note}  

É possível optar por alocar os endereços IP públicos do balanceador de carga de um conjunto do sistema IBM (padrão) ou de uma VLAN pública sob sua conta ao
criar sua instância de serviço de balanceador de carga.

## Balanceador de carga interno
{: #internal-load-balancer}

O balanceador de carga interno é acessível apenas dentro da rede privada do IBM Cloud.

Assim como acontece com um balanceador de carga público, um nome completo do domínio também é designado à sua instância de serviço do balanceador de carga interno. Entretanto, esse nome de domínio é registrado com um ou mais endereços IP privados.

Semelhante a um balanceador de carga público, os endereços IP privados e seus números podem mudar ao longo do tempo com base em atividades de manutenção e ajuste de escala, que são transparentes para os usuários finais.

As instâncias de cálculo de backend que hospedam seu aplicativo também devem estar na rede privada do IBM Cloud.
{: note}

## Portas/Protocolos dos aplicativos front-end e backend
{: #front-end-and-back-end-application-ports-protocols}

É possível definir até dez portas (protocolos) do aplicativo front-end e mapeá-las para as respectivas portas (protocolos) nos servidores de aplicativos back-end. O nome completo do domínio designado à instância do serviço do balanceador de carga e as portas do aplicativo front-end são expostos ao mundo externo. As solicitações recebidas de usuários são recebidas nessas portas.

Por outro lado, as portas de back-end são conhecidas apenas internamente. Essas portas de back-end podem ou não ser as mesmas que as portas de front-end. Como exemplo, o balanceador de carga pode ser configurado para receber o tráfego web/HTTP recebido na porta de front-end 80, enquanto os servidores de back-end estão atendendo na porta customizada 81.

As portas/protocolos de front-end suportados são HTTP, HTTPS e TCP. As portas/os protocolos de back-end suportados também são HTTP, HTTPS e TCP. O tráfego HTTPS recebido deve ser finalizado no balanceador de carga para permitir a comunicação HTTP de texto sem formatação com o servidor de backend. Se o protocolo de back-end for HTTPS, o tráfego será criptografado entre o balanceador de carga e os servidores de back-end.

### Considerações
{: #considerations}

* Durante a configuração inicial, é possível definir até duas portas de front-end apenas. Quando um balanceador de carga é criado, é possível editar a configuração de porta para definir portas adicionais, até o máximo de dez portas.
* As dez portas de front-end deverão ser mapeadas para o mesmo conjunto de instâncias do servidor de back-end.
* O número máximo de instâncias do servidor que podem ser colocadas atrás de um balanceador de carga é 50.
* O intervalo de portas de 56.500 a 56.520 é reservado para propósitos de gerenciamento e não pode ser usado como portas virtuais de front-end.
* A porta TCP 56501 é usada para gerenciamento. Se você optar por alocar endereços IP públicos de balanceador de carga de sua VLAN pública, assegure-se de que o tráfego para essa porta de gerenciamento, bem como para as portas de seu aplicativo, não seja bloqueado por quaisquer firewalls que você possa ter implementado em suas VLANs públicas. Isso não será necessário se você escolher a opção do conjunto do sistema IBM para alocar endereços IP públicos de balanceador de carga.

## Métodos de balanceamento de carga
{: #load-balancing-methods}

Os três métodos de balanceamento de carga a seguir estão disponíveis para distribuir tráfego entre servidores de aplicativos back-end:

* **Round-robin:** é o método de balanceamento de carga padrão. Com esse método, o balanceador de carga encaminha conexões do cliente recebidas no modo round-robin para os servidores de back-end. Como resultado, todos os servidores de back-end recebem praticamente um número igual de conexões do cliente.

* **Round-robin ponderado:** com esse método, o balanceador de carga encaminha conexões de cliente recebidas para os servidores de back-end em proporção ao peso designado a esses servidores. A cada servidor é designado um peso padrão de 50, que pode ser customizado para qualquer valor entre 0 e 100.

	Como exemplo, se houver três servidores de aplicativos A, B e C e seus pesos forem customizados para 60, 60 e 30, respectivamente, os servidores A e B receberão um número igual de conexões, enquanto o servidor C receberá metade desse número de conexões.


	Reconfigurar o peso de um servidor para '0' significa que nenhuma nova conexão será encaminhada para esse servidor, mas qualquer tráfego existente continuará fluindo enquanto ele estiver ativo. Usar um peso de '0' pode ajudar a desativar um servidor normalmente e removê-lo da rotação de serviço.
	{: note}

	Os valores de ponderação do servidor são aplicáveis apenas com o método 'round-robin ponderado'. Eles são ignorados com os métodos de balanceamento de carga 'round-robin' e 'menos conexões'.
	{: note}

* **Menos conexões:** com esse método, a instância do servidor que entrega o menor número de conexões em um determinado momento recebe a conexão do próximo cliente.

## Escala horizontal
{: #horizontal-scaling}

O balanceador de carga ajusta sua capacidade automaticamente de acordo com a carga. Quando isso ocorre, é possível ver uma mudança no número de endereços IP associados ao nome DNS do balanceador de carga.
