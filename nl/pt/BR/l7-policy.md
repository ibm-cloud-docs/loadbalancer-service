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

# Política da Camada 7

Uma política da Camada 7 (L7) é usada para classificar o tráfego, correspondendo suas informações da L7 com as regras da L7 e, em seguida, tomando ações específicas no caso de correspondência das regras. 

* Uma política é aplicada a uma porta de aplicativo front-end (protocolo). 
* Várias políticas podem ser aplicadas ao mesmo protocolo.

Como várias políticas podem ser aplicadas a um protocolo, há uma prioridade associada a cada política. 

* As políticas com a prioridade configurada mais baixa são avaliadas primeiro. 
* Se as regras associadas à política não corresponderem ao tráfego, a próxima política mais baixa na lista de prioridades será avaliada. 

Se o tráfego não corresponder a nenhuma das regras de política, o tráfego será redirecionado para um conjunto padrão, que é aquele configurado quando o balanceador de carga básico foi implementado.

Cada política é associada a uma ação que é executada quando todas as regras na política correspondem ao tráfego.

As ações podem ser:

- Rejeitar 
- Redirecionar para uma URL
- Redirecionar para o conjunto 

As políticas configuradas como `reject` são avaliadas primeiro, independentemente de sua prioridade.

Depois disso, as políticas configuradas como `redirect to url` são avaliadas.

Finalmente, as políticas configuradas como `redirect to pool` são avaliadas.

Dentro de cada categoria de ação, as políticas são avaliadas em ordem crescente de prioridade (mais baixa para a mais alta).

## Propriedades da política da Camada 7

Propriedade  | Descrição
------------- | -------------
Nome | O nome da política. Cada política deve ter um nome exclusivo.
Ação | A ação a ser tomada quando as regras corresponderem. As ações são `REJECT`, `REDIRECT_URL` e `REDIRECT_POOL`. Uma política cuja ação está configurada como `REJECT` é sempre avaliada primeiro, independentemente de sua prioridade. As políticas cujas ações estão configuradas como `REDIRECT_URL` são as próximas a serem avaliadas, seguidas por políticas cujas ações estão configuradas como `REDIRECT_POOL`.
Prioridade | As políticas são avaliadas com base na ordem crescente de prioridade. 
Redirecionar URL | A URL para a qual o tráfego será redirecionado, se a ação estiver configurada como `REDIRECT_URL`.
Redirecionar conjunto da L7 | O conjunto de servidores para o qual o tráfego será enviado, se a ação estiver configurada como `REDIRECT_POOL`.
Protocolo | A porta do aplicativo front-end à qual a política é aplicada.

# Regra da Camada 7
As regras da Camada 7 definem uma parte do tráfego recebido que deve ser correspondida com valores específicos.

* Se o tráfego recebido corresponder ao valor especificado de uma regra, a regra será avaliada como `true`.
* As regras da camada 7 são sempre associadas a uma política da Camada 7. Várias regras da Camada 7 podem ser associadas à mesma política da camada 7.
* Se várias regras estiverem associadas a uma política, cada regra será avaliada como `true` ou `false`. 
* Se todas as regras associadas a uma política forem avaliadas como `true`, a ação de política será aplicada à solicitação. Caso contrário, o balanceador de carga avaliará a próxima política.

As regras têm tipos, que podem ser: 

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

Eles indicam a parte do tráfego da Camada 7 a ser correspondida com a regra.

Tipo      |  Campo a ser extraído e avaliado
----------| -----------------------
`HOST_NAME` | A parte de nome do host da URL (por exemplo, `api.my_company.com`)
`FILE_TYPE` | O final da URL, que representa o tipo de arquivo (por exemplo, `jpg`)
HEADER    | Um campo no cabeçalho de HTTP
COOKIE    | Um cookie especificado no cabeçalho de HTTP 
PATH      | A parte da URL que segue o nome do host (por exemplo, `/index.html`)

As regras também têm um tipo de comparação, que indica como elas devem ser avaliadas.
As regras podem ter os tipos de comparação a seguir: 

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

Tipo de comparação |  Tipo de avaliação
----------------|---------------------
`REGEX`           |  Corresponder o campo extraído (por exemplo, `hostname`) com a expressão regular fornecida
`STARTS_WITH`     |  Verificar se o campo extraído inicia com a sequência fornecida
`ENDS_WITH`       |  Verificar se o campo extraído termina com a sequência fornecida
`CONTAINS`        |  Verificar se o campo extraído contém a sequência fornecida
`EQUAL_TO`        |  Verificar se o campo extraído é idêntico à sequência fornecida

**NOTA**: nem todos os tipos de regra suportam todos os tipos de comparação. Por exemplo, se você estiver usando `FILE_TYPE`, será melhor usar os tipos de comparação `REGEX` e `ENDS_WITH`.

## Propriedades de regra da Camada 7

Propriedade  | Descrição
------------- | -------------
Tipo | Especifica o tipo de regra. Os tipos de regra podem ser `HOST_NAME` (o nome do host), `FILE_TYPE` (o tipo do arquivo), `HEADER` (o cabeçalho), `COOKIE` (o cookie) ou `PATH` (o caminho).
Tipo de comparação | Os tipos de comparação são usados em associação ao tipo de regra, chave e valor para definir uma regra e classificar o tráfego. Os tipos de comparações podem ser: `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS` e `EQUAL_TO`.
Chave | A chave de descrição para os tipos de regra `HEADER` e `COOKIE`. 
Valor |  Para os tipos de regra `HEADER` e `COOKIE`, o valor é comparado com a chave.
Inverter | Se você configurar o valor como 1, o valor dessa comparação de regra da L7 será configurado como `true` sempre que a regra especificada não for correspondida.
ID de política da Camada 7 | O identificador exclusivo da política à qual as regras estão anexadas.
