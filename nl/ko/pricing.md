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


# 가격 책정

IBM Cloud 로드 밸런서 가격 책정은 월별 계산되는 다음의 3개 메트릭을 기반으로 합니다.

* 서비스 사용 시간
* 처리된 데이터
* 아웃바운드 공용 대역폭(Egress)

**참고:** 모든 가격은 지리적 위치별로 다양합니다. IBM Cloud Load Balancer Service에서 이용하는 아웃바운드 공용 대역폭은 [USD $0.09/GB ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/bandwidth)의 표준 데이터 전송 비용에 따라 청구됩니다.

다음 차트는 공용 로드 밸런싱에 매월 4,500GB를 사용하는 고객에 대해 가격 책정된 IBM Cloud 로드 밸런서의 예를 상세히 보여줍니다.

| | 월별 |요금 | 비용 |
| ------------- | ------------- | ------------- | ------------- |
| **서비스 사용** | 720시간 | $0.025/시간 | $18/월 |
| **처리된 데이터** | 4,500GB | $0.008/GB | $36/월 |

위의 시나리오에 대한 비용 총계는 $54/월 + 표준 데이터 전송 비용 [USD $0.09/GB ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/bandwidth)입니다.

![가격 책정](./images/pricing.png)


**참고:** 모든 가격은 지리적 위치별로 다양합니다. 다이어그램과 예에서의 가격 책정은 댈러스 시의 가격 책정입니다(미국 달러). $0.025/시간의 서비스 사용 요금은 다이어그램에 표시되어 있지 않습니다.

사용자 지역에 대한 특정 가격 책정 정보를 보기 위해 간단한 [가입 프로세스](https://console.bluemix.net/catalog/infrastructure/load-balancer-group)를 거쳐야 할 수 있습니다.
