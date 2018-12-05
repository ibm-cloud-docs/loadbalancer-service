---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Resolução de problemas da mensagem de erro
Este tópico fornece informações sobre mensagens de erro comuns que podem ser encontradas ao criar/atualizar uma instância do IBM Cloud Load Balancer.

| Erro | Explicação  | Solução  |
| ------------- | ------------- | ----- |
| `O número máximo de balanceadores de carga `n` foi atingido.`| Permitimos apenas 50 instâncias do balanceador de carga por conta. | Assegure-se de que tenha 50 ou menos instâncias do Load Balancer por conta. |
| `O número máximo de protocolos fornecidos `n` no pedido do produto do balanceador de carga foi atingido.` | Apenas dois protocolos podem ser incluídos ao provisionar um Load Balancer.  | Se mais protocolos forem necessários, após o fornecimento, será possível incluir até dez por meio da guia **Protocolos** no fluxo de gerenciamento do Load Balancer. Para obter mais informações, consulte [Monitorando e gerenciando seu serviço](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service). |
| `O número máximo de instâncias de servidor especificadas `n` no pedido do produto do balanceador de carga foi atingido.` | Apenas dez servidores podem ser incluídos ao provisionar um Load Balancer. | Se forem necessários servidores adicionais, após o fornecimento, será possível incluir até 50 por meio da guia **Instâncias do servidor** no fluxo de gerenciamento do Load Balancer. Para obter mais informações, consulte [Monitorando e gerenciando seu serviço](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service). |
| `O nome do balanceador de carga deve ser uma sequência e ter pelo menos 1 e até 40 caracteres.` | O nome do Load Balancer é obrigatório. Use apenas caracteres alfanuméricos (ou os caracteres especiais '-' e '.') para o nome. O nome não deve iniciar ou terminar com um caractere especial e deve ser limitado a 40 caracteres de comprimento. | Insira um nome exclusivo para o Load Balancer. Por exemplo, "ui-servers" ou "backend-servers".|
| `Erro de formatação localizado no nome do balanceador de carga especificado.` O nome do Load Balancer é obrigatório. Use apenas caracteres alfanuméricos (ou os caracteres especiais '-' e '.') para o nome. O nome não deve iniciar ou terminar com um caractere especial e deve ser limitado a 40 caracteres de comprimento. | Insira um nome exclusivo para o Load Balancer. Por exemplo, "ui-servers" ou "backend-servers".|
| Já existe um balanceador de carga com o mesmo nome (sem distinção entre maiúsculas e minúsculas). | Existe um balanceador de carga com o mesmo nome. | Insira um nome de balanceador de carga exclusivo para continuar. Por exemplo, ui-servers, backend-servers etc. |
| A descrição do balanceador de carga deve ser uma sequência e não deve exceder 255 caracteres. | A descrição do balanceador de carga deve ser uma sequência e não deve exceder 255 caracteres. | Insira uma descrição de balanceador de carga válida dentro de 255 caracteres. |
| A porta front-end `80` já está sendo usada. | Talvez você tenha inserido uma porta front-end duplicada que já está sendo usada. | Insira uma porta front-end exclusiva. |
| A porta back-end deve ser um número inteiro. | Talvez você tenha inserido um valor de porta de back-end inválido. | Insira uma porta de back-end válida entre 1 e 65535. |
|Uma vez que o protocolo e a porta não são editáveis no monitor de funcionamento, esse erro é impossível na IU.| A sub-rede privada `xyz` não é do tipo padrão e, portanto, não pode ser usada para criar balanceador de carga.|Entre em contato com o suporte IBM.|
|A sub-rede privada `xyz` deve ter pelo menos `n` endereços IP livres.|A sub-rede privada selecionada não está tendo endereços IP livres.|Verifique estas [etapas de resolução de problemas](/docs/infrastructure/loadbalancer-service/troubleshooting-provisioning.html#insufficient-ip-addresses-in-your-subnet) para obter mais detalhes.|
|A VLAN da sub-rede privada especificada está no roteador `xyz`. No entanto, nenhuma VLAN pública com `n` IPs livres foi localizada no mesmo roteador.|Isso acontece porque você selecionou a opção "Alocar na sub-rede pública por meio desta conta" durante o fornecimento.|Selecione a opção "Alocar no Conjunto de sistemas IBM" ou entre em contato com o suporte IBM.|
|A VLAN da sub-rede privada especificada está no roteador `xyz`. No entanto, nenhuma sub-rede pública com `n` IPs livres foi localizada com VLAN no mesmo roteador.|Isso acontece porque você selecionou a opção "Alocar na sub-rede pública por meio desta conta" durante o fornecimento.|Selecione a opção "Alocar no Conjunto de sistemas IBM" ou entre em contato com o suporte IBM.|
|Dada a nova descrição, deve ser uma sequência.|Talvez você tenha inserido uma descrição inválida.|Insira uma descrição válida do balanceador de carga com menos de 255 caracteres.|
|É necessário um item de faturamento para processar um cancelamento para o balanceador de carga uuid=`aaaa-bbbb-cccc-dddd`.| | Entre em contato com o suporte IBM.|
|Ocorreu um erro interno. Os dados não puderam ser recuperados.|Dados de métricas não podem ser recuperados|Recarregue a página. Se o problema ainda persistir, entre em contato com o suporte IBM.|
|A porta front-end deve ser um número inteiro entre 1 e 65535, excluindo o intervalo de 56500 a 56520.|Talvez você tenha inserido uma porta front-end entre 56500 e 56520. |Insira qualquer outra porta exclusiva entre 1 e 65535, excluindo o intervalo de 56500 a 56520.|
|A porta back-end deve ser um número inteiro.|Talvez você tenha inserido um valor de porta de back-end inválido.|Insira uma porta de back-end válida entre 1 e 65535.|
|A porta back-end deve ser um número inteiro entre 1 e 65535, excluindo o intervalo de 56500 a 56520.|Talvez você tenha inserido uma porta back-end entre 56500 e 56520. |Insira qualquer outra porta back-end válida entre 1 e 65535, excluindo o intervalo de 56500 a 56520.|
|O protocolo de back-end `HTTP` não é compatível com o protocolo de front-end `TCP`.|Talvez você tenha selecionado uma combinação incompatível de protocolo de back-end e protocolo de front-end.|Selecione uma combinação válida de protocolos de front-end e back-end como abaixo: <br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP|
|O peso do membro `<some value>` é fornecido para o membro `abcd-xxxx-yyyy-2222`. O valor de peso permitido é de 0 a 100|Talvez você tenha inserido um peso inválido.|Insira um peso entre 0 e 100.|
|Houve um problema ao buscar os servidores.|Isso pode acontecer devido a problemas de tempo limite da rede.| Recarregue a página. Se o problema ainda persistir, entre em contato com o suporte IBM.|
