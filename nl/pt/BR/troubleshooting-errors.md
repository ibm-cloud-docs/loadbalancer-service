---

copyright:
  years: 2018
lastupdated: "2018-11-21"

keywords: error, message, troubleshooting, problems

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Resolução de problemas da mensagem de erro
{: #error-message-troubleshooting}

Este tópico fornece informações sobre mensagens de erro comuns que você pode encontrar ao
criar/atualizar uma instância do {{site.data.keyword.loadbalancer_full}}.

| Erro | Explicação  | Solução  |
| ------------- | ------------- | ----- |
| `O número máximo de balanceadores de carga `n` foi atingido.`| Permitimos apenas 50 instâncias do balanceador de carga por conta. | Assegure-se de que tenha 50 ou menos instâncias do Load Balancer por conta. |
| `O número máximo de protocolos fornecidos `n` no pedido do produto do balanceador de carga foi atingido.` | Apenas dois protocolos podem ser incluídos ao provisionar um Load Balancer.  | Se mais protocolos forem necessários, após o fornecimento, será possível incluir até dez por meio da guia **Protocolos** no fluxo de gerenciamento do Load Balancer. Para obter mais informações, consulte [Monitorando e gerenciando seu serviço](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `O número máximo de instâncias de servidor especificadas `n` no pedido do produto do balanceador de carga foi atingido.` | Apenas dez servidores podem ser incluídos ao provisionar um Load Balancer. | Se forem necessários servidores adicionais, após o fornecimento, será possível incluir até 50 por meio da guia **Instâncias do servidor** no fluxo de gerenciamento do Load Balancer. Para obter mais informações, consulte [Monitorando e gerenciando seu serviço](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `O nome do balanceador de carga deve ser uma sequência e ter pelo menos 1 e até 40 caracteres.` | O nome do Load Balancer é obrigatório. Use apenas caracteres alfanuméricos (ou os caracteres especiais '-' e '.') para o nome. O nome não deve iniciar ou terminar com um caractere especial e deve ser limitado a 40 caracteres de comprimento. | Insira um nome exclusivo para o Load Balancer. Por exemplo, "ui-servers" ou "backend-servers".|
| `Erro de formatação localizado no nome do balanceador de carga especificado.` | O nome do Load Balancer é obrigatório. Use apenas caracteres alfanuméricos (ou os caracteres especiais '-' e '.') para o nome. O nome não deve iniciar ou terminar com um caractere especial e deve ser limitado a 40 caracteres de comprimento. | Insira um nome exclusivo para o Load Balancer. Por exemplo, "ui-servers" ou "backend-servers".|
| `Já existe um balanceador de carga com o mesmo nome (sem distinção entre maiúsculas e minúsculas).` | Existe um balanceador de carga com o mesmo nome. | Insira um nome exclusivo do Balanceador de Carga para continuar, por
exemplo, "ui-servers" ou "backend-servers". |
| `A descrição do balanceador de carga deve ser uma sequência e não exceder 255 caracteres.` | A descrição do Balanceador de Carga deve ser uma sequência que não exceda 255 caracteres. | Limite a descrição a 255 caracteres. |
| `A porta de front-end 80 já está sendo usada.` | Você pode ter inserido uma porta de
front-end que já está em uso. | Insira uma porta de front-end exclusiva. |
| `A porta de back-end deve ser um número inteiro.` | Você pode ter inserido um valor de porta de back-end inválido. | Insira um número de porta de back-end entre 1 e 65535. |
| `Como o protocolo e a porta não são editáveis no monitor de funcionamento, esse erro é impossível
na IU.`| A sua sub-rede privada não é um tipo padrão e não pode ser usada para criar o
Balanceador de Carga. | Entre em contato com o suporte IBM. |
| A `Sub-rede privada `xyz` deve ter pelo menos `n`
endereços IP livres.` | A sub-rede privada selecionada não tem nenhum endereço IP livre. | Verifique essas [etapas
de resolução de problemas](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting) para obter mais informações. |
| `A VLAN da sub-rede privada especificada está no roteador `xyz`. No entanto,
nenhuma VLAN pública com `n` IPs livres foi localizada no mesmo roteador.` | Isso acontece porque você selecionou a opção **Alocar na sub-rede pública nesta conta** durante
o fornecimento. | Selecione **Alocar no IBM System Pool** em vez disso ou entre em contato com o Suporte IBM.|
| `A VLAN da sub-rede privada especificada está no roteador `xyz`. No entanto,
nenhuma sub-rede pública com `n` IPs livres foi localizada com VLAN no mesmo roteador. ` | Isso acontece porque você selecionou a opção **Alocar na sub-rede pública nesta conta** durante
o fornecimento. | Selecione **Alocar no IBM System Pool** em vez disso ou entre em contato com o Suporte IBM.|
| `Dada a nova descrição, deve ser uma sequência.`| Você pode ter inserido uma descrição inválida. | Insira uma descrição válida do Balanceador de Carga, com no máximo 255 caracteres. |
| `Um item de faturamento é requerido para processar um cancelamento para o balanceador de
carga uuid=aaaa-bbbb-cccc-dddd.` | As informações de faturamento estão ausentes ou são
inválidas para sua conta e o Balanceador de Carga não pode ser cancelado. | Entre em contato com o suporte IBM.|
| `Ocorreu um erro interno. Os dados não puderam ser recuperados.` | Os dados de métrica
não podem ser recuperados | Recarregue a página. Se o problema ainda persistir, entre em contato com o suporte IBM. |
| `A porta de front-end deve ser um número inteiro entre 1 e 65535, excluindo o intervalo de 56500-56520.` | Você pode ter inserido um número de porta front-end entre 56500-56520. | Insira um número de porta exclusivo entre 1 a 65535, mas excluindo o intervalo de 56500 a 56520. |
| `A porta de back-end deve ser um número inteiro.` | Você pode ter inserido um valor de porta de back-end inválido. | Insira um número de porta de back-end entre 1 e 65535. |
| `A porta de back-end deve ser um número inteiro entre 1 e 65535, excluindo o intervalo de 56500-56520.` | Você pode ter inserido uma porta back-end entre 56500 e 56520.| Insira um número de porta de back-end
entre 1 e 65535, mas excluindo o intervalo de 56500 a 56520. |
| `O HTTP de protocolo de back-end não é compatível com o TCP do protocolo de front-end.` | Você pode ter selecionado um protocolo de back-end incompatível e uma combinação de protocolo de front-end. | Selecione uma combinação válida de protocolo de front-end e back-end, no formato: `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Member weight <some value> é fornecido para o membro abcd-xxxx-yyyy-2222. O valor do peso
permitido é 0-100 `| Você pode ter inserido um peso inválido. | Insira um valor de peso entre 0 e 100. |
| `Ocorreu um problema ao buscar os servidores.` | Isso pode acontecer como um resultado de problemas de tempo limite de rede. | Recarregue a página. Se o problema ainda persistir, entre em contato
com o Suporte IBM.|
