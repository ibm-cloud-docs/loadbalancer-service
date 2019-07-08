---

copyright:
  years: 2017, 2018
lastupdated: "2019-02-19"

keywords: updates, additions, imporvements

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

# IBM Cloud Load Balancer의 최신 업데이트
{: #recent-updates-for-ibm-cloud-load-balancer}

IBM© Cloud 로드 밸런서의 새 기능과 업데이트된 기능에 대해 알아봅니다.

## 2019년 2월
{: #february-2019}

### 데이터 로그
{: #data-logs}

이제 IBM Cloud Load Balancer가 데이터 로그 전달을 지원합니다. 데이터 로그가 사용으로 설정되면 로드 밸런서 로그 데이터가 [IBM Cloud 로그 분석 서비스![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}에 전달됩니다. 고객은 [IBM Cloud 로그 분석 서비스![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}에서 데이터 로그를 볼 수 있습니다. 

## 2018년 12월
{: #december-2018}

### 백엔드 암호화 및 데이터 로그 전달
{: #backend-encryption-and-data-log-forwarding}

IBM Cloud Load Balancer에서는 이제 백엔드 암호화와 데이터 로그를 전달하는 기능을 지원합니다. 백엔드 암호화를 사용하면 로드 밸런서와 백엔드 서버 사이의 트래픽을 포함하여 엔드 투 엔드 데이터 트래픽 암호화가 가능합니다. 데이터 로그 전달을 사용하면 로드 밸런서에서 IBM Bluemix Log Analysis Service로 데이터 로그를 보낼 수 있습니다.

## 2018년 8월
{: #august-2018}

### 계층 7 지원
{: #layer-7-support-1}

이제 IBM Cloud Load Balancer가 계층 7 로드 밸런싱을 지원합니다. 계층 7(L7) 지원을 사용하면 트래픽을 URL로 경로 재지정하거나, 거부하거나, Bare Metal 및 Virtual Server 인스턴스를 포함한 L7 풀 멤버에 분배할 수 있습니다. 수신 데이터 트래픽은 계층 7 정책 및 규칙을 사용하여 분류됩니다. 정책은 데이터 트래픽이 정책과 연관된 규칙과 일치하는 경우 수행할 조치를 정의합니다.

추가 세부사항은 [계층 7 로드 밸런싱](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing)을 참조하십시오.

## 2018년 4월
{: #april-2018}

### 수평적 확장
{: #horizontal-scaling}

이제 IBM Cloud Load Balancer는 로드가 증가하면 자동으로 확장되며 로드가 감소하면 축소됩니다. 로드 밸런서를 작성할 때 두 개의 어플라이언스로 시작되지만 모니터링 시스템이 로드 증가를 감지하면 어플라이언스의 수가 16개로 증가될 수 있습니다(이 문서 작성 시점 기준). 각 활성 어플라이언스의 IP 주소는 DNS A-레코드로서 로드 밸런서의 완전한 도메인 이름(FQDN)에 추가됩니다.

### 내부 로드 밸런서
{: #internal-load-balancer-1}

과도한 수요의 "내부" 버전의 IBM Cloud Load Balancer를 현재 사용할 수 있습니다. 이 로드 밸런서는 공개적으로 노출되지 않지만 여전히 IBM Cloud 사설 네트워크 내에서 애플리케이션을 밸런싱하는 데 사용될 수 있습니다(예를 들어, 그림에 표시된 대로 다중 티어 배치에서).

![내부 로드 밸런서](./images/InternalLB.png)

이는 공용 측면에서 보안성은 물론 이전 IBM Cloud Load Balancer 버전과의 일관성도 제공합니다.

### 모니터링 메트릭
{: #monitoring-metrics-2}

이제 “IBM Cloud Monitoring” 서비스를 최대한 활용하여 로드 밸런서 및 애플리케이션과 연관된 다음의 성능 메트릭을 모니터할 수 있습니다.

* 처리량
* 연결 속도
* 활성 연결 수

![모니터링 메트릭](./images/Metrics.png)

최대 2주 간의 샘플이 로드 밸런서 웹 UI에 의해 수집되고 표시됩니다. 데이터를 IBM Cloud Monitoring 서비스 포털에서 볼 수도 있습니다. 2주를 초과하는 기간의 데이터가 필요한 경우에는 Cloud Monitoring 인스턴스에 전송 중인 기타 클라우드 메트릭의 볼륨에 따라 모니터링 플랜을 업그레이드해야 할 수 있습니다. 추가 세부사항은 [모니터링 메트릭](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer)을 참조하십시오.

이 기능을 사용하려면 몇 가지 [간단한 단계](/docs/account?topic=account-unifyingaccounts)를 사용하여 IBM Cloud IaaS와 PaaS 계정을 연결해야 합니다.

### 암호 스위트 사용자 정의
{: #cipher-suite-custom-1}

이제 SSL 종료를 위해 로드 밸런서가 구성될 때 사용되는 암호 스위트를 사용자 정의할 수 있습니다.

IBM Cloud Load Balancer에서 SSL 종료를 사용하는 경우(**HTTPS**를 프론트 엔드 프로토콜로 선택하여) 보안 우수 사례를 준수하는 신중하게 선택된 기본 암호 스위트 세트가 사용됩니다. IBM에서는 감지될 수 있는 새로운 취약점을 면밀히 감시하며 이에 따라 목록을 업데이트합니다. 이는 소프트웨어 및 하드웨어 컴포넌트의 완벽한 보안 업데이트와 함께 항상 애플리케이션의 보안을 유지하는 데 도움이 됩니다.

추가 세부사항은 [사용자 정의 암호화 스위트](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application)를 참조하십시오.
