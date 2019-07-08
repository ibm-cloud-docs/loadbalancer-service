---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, metrics, throughput, connection

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

# IBM Cloud Load Balancer로 메트릭 모니터링
{: #monitoring-metrics-with-ibm-cloud-load-balancer}

로드 밸런서는 다음의 메트릭을 모니터합니다.

* 처리량
* 활성 연결 수
* 연결 속도

이러한 메트릭은 **모니터링** 탭을 선택하여 볼 수 있는 그래프로서 시각적으로 표시되며,
`getListenerTimeSeriesData` API를 사용하여 시계열 데이터 점으로서 프로그래밍 방식으로 사용 가능합니다.

각 데이터 점에는 UNIX epoch 시간의 시간소인과 함께 이 시간소인에 끝나는 해당 시간 간격의 메트릭 값이 포함되어 있습니다. 사용자는 메트릭이 보고되는 시간 간격과 프로토콜을 지정할 수 있습니다.

지원되는 프로토콜에는 다음이 포함됩니다.

* HTTP
* HTTPS
* TCP

프로토콜을 지정하면 해당 프로토콜로 메트릭이 필터링됩니다.

예를 들어, 프로토콜이 지정되지 않았으며 메트릭이 *처리량*인 경우에는 모든 프로토콜의 처리량 총계가 보고됩니다.

프로토콜이 *HTTP*인 경우에는 HTTP 트래픽에 대한 처리량만 보고됩니다.

사용자는 메트릭이 보고되는 시간 간격을 지정할 수도 있습니다. 지원되는 시간 간격은 다음과 같습니다.

* 1시간
* 6시간
* 12시간
* 24시간
* 1주
* 2주

보고된 데이터 점의 수는 각 시간 간격마다 개략적으로 동일합니다.  
예를 들어, 간격이 1시간이면 각 데이터 점이 5분의 데이터를 표시합니다.

간격이 2주인 경우에는 각 데이터 점이 24시간의 데이터를 표시합니다.

아래의 표에는 시간 간격에서 데이터 점이 파생되는 방법이 표시되어 있습니다.

| 시간 간격 | 데이터 점 정밀도 | 데이터 점의 수 |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1시간    | 5분 | 12   |
| 6시간   | 30분 | 12  |
| 12시간  | 1시간 | 12 |
| 24시간  | 2시간 | 12 |
| 1주    | 12시간 | 12 |
| 2주  | 24시간 | 12 |

## 모니터링 메트릭 사용법
{: #how-to-enable-metrics-monitoring}

모니터링 메트릭을 검색하려면 SoftLayer 계정을 IBM© Cloud 계정과 연결해야 합니다. 자세한 정보는 [이 주제](/docs/account?topic=account-unifyingaccounts#link_accounts)를 참조하십시오.
