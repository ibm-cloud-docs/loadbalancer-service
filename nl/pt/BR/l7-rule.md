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

# Regras da Camada 7
{: #layer-7-rules}

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

As regras também possuem um tipo de comparação, que indica como elas devem ser avaliadas. 
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
