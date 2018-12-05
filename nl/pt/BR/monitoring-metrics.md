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

# Monitorando métricas

O balanceador de carga monitora as métricas a seguir: 

* Rendimento
* Conexões ativas
* Taxa de conexão

Essas métricas são visualizadas como gráficos que podem ser visualizados selecionando a guia **Monitoramento** e estão disponíveis programaticamente como pontos de dados da série temporal, usando a API `getListenerTimeSeriesData`.

Cada ponto de dados contém um registro de data e hora na época do UNIX e o valor da métrica para esse intervalo de tempo terminando nesse registro de data e hora. O usuário pode especificar os protocolos e o intervalo de tempo durante o qual as métricas devem ser relatadas. 

Os protocolos suportados incluem:

* HTTP
* HTTPS
* TCP

Especificar um protocolo filtra a métrica por esse protocolo.

Por exemplo, se nenhum protocolo for especificado e a métrica for *Rendimento*, o rendimento total de todos os protocolos será relatado.

Se o protocolo for *HTTP*, apenas o rendimento para o tráfego de HTTP será relatado.

O usuário também pode especificar o intervalo de tempo sobre o qual a métrica deve ser relatada. Os intervalos de tempo suportados são: 

* 1 hora
* 6 horas
* 12 horas
* 24 horas
* 1 semana
* 2 semanas

O número de pontos de dados relatados é aproximadamente o mesmo para cada intervalo de tempo.  
Por exemplo, se o intervalo for 1 hora, cada ponto de dados representará 5 minutos de dados.

Se o intervalo for de 2 semanas, cada ponto de dados representará 24 horas de dados.

A tabela abaixo mostra como os pontos de dados são derivados do intervalo de tempo:

| Intervalo de tempo | Precisão de ponto de dados | Número de pontos de dados |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1 hora    | 5 minutos | 12   |
| 6 horas   | 30 minutos | 12  |
| 12 horas  | 1 hora | 12 |
| 24 horas  | 2 horas | 12 |
| 1 semana    | 12 horas | 12 |
| 2 semanas  | 24 horas | 12 |

# Como ativar o monitoramento de métricas

Para recuperar as métricas de monitoramento, deve-se vincular sua conta do SoftLayer à sua conta do IBM Cloud. Consulte [este tópico ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/account/softlayerlink.html#link_user_account) para obter mais informações.
