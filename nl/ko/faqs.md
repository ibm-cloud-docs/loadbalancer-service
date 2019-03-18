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

# IBM Cloud Load Balancer의 FAQ
{: #faqs-for-ibm-cloud-load-balancer}

이 절에는 IBM© Cloud Load Balancer Service와 관련하여 일부 자주 묻는 질문에 대한 답변이 포함되어 있습니다.

## {{site.data.keyword.BluSoftlayer_notm}}에서 사용 가능한 로드 밸런싱 옵션은 몇 가지입니까?
{:faq}

IBM의 Load Balancers 오퍼링에 대한 자세한 비교를 보려면 [Load Balancers 탐색](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-explore)을 참조하십시오.

## 내 로드 밸런서에 대해 다른 DNS 이름을 사용할 수 있습니까?
{:faq}

로드 밸런서에 대해 자동 지정된 DNS 이름은 사용자 정의할 수 없지만 자동 지정된 로드 밸런서 DNS 이름에 선호하는 DNS 이름을 가리키는 CNAME(표준 이름) 레코드를 추가할 수 있습니다. 

예를 들어, 계정 번호가 123456이고, 로드 밸런서가 `dal09` 데이터 센터에 배치되고 이름이 `myapp`이며 자동 지정된 로드 밸런서 DNS 이름이 `myapp-123456-dal09.lb.bluemix.net`인 경우가 있습니다. 선호하는 DNS 이름은 `www.myapp.com`입니다. 로드 밸런서 DNS 이름 myapp-12345-dal09.lb.bluemix.net에 `www.myapp.com`을 가리키는 CNAME 레코드(myapp.com을 관리하는 데 사용하는 DNS 제공자 경유)를 추가할 수 있습니다.

## 내 로드 밸런서 서비스를 사용하여 정의할 수 있는 최대 가상 포트는 몇 개입니까?
{:faq}

새 로드 밸런서 서비스를 작성하면서 최대 두 개의 가상 포트를 정의할 수 있습니다. 서비스가 작성된 후에는 추가 가상 포트를 정의할 수 있습니다. 허용되는 최대 가상 포트 수는 10입니다.

## 내 로드 밸런서와 연관시킬 수 있는 최대 컴퓨팅 인스턴스는 몇 개입니까?
{:faq}

50.

## 내 백엔드 컴퓨팅 인스턴스가 로드 밸런서의 서브넷과 다른 서브넷에 있을 수 있습니까?
{:faq}

예, 로드 밸런서 및 로드 밸런서에 연결된 컴퓨팅 인스턴스는 다른 서브넷에 있을 수 있지만 로드 밸런서가 컴퓨팅 인스턴스와 통신하고 컴퓨팅 인스턴스에 요청을 전달하려면 **VLAN Spanning**이 사용으로 설정되어야 합니다. 자세한 정보는 [VLAN Spanning 문제점 해결](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-vlan-spanning-troubleshooting)을 참조하십시오.

## 여러 상태 검사 매개변수에 대한 기본 설정 및 허용된 값은 무엇입니까?
{:faq}

기본 설정 및 허용된 값은 다음과 같습니다.

* **상태 검사 간격:** 기본값은 5초이고, 범위는 2 – 60초입니다.
* **상태 검사 응답 제한시간:** 기본값은 2초이고, 범위는 1 – 59초입니다.
* **최대 재시도 횟수:** 기본값은 2회 재시도이고 범위는 1 - 10회 재시도입니다.

**참고:** 상태 검사 응답 제한시간 값은 항상 상태 검사 간격 값 미만이어야 합니다.

## 이 서비스를 사용하여 원격 데이터 센터에 상주하는 컴퓨팅 인스턴스를 사용할 수 있습니까?
{:faq}

로드 밸런서 서비스 및 컴퓨팅 인스턴스를 동일한 데이터 센터 내에 로컬로 상주시키도록 권장합니다. 로드 밸런서 서비스의 그래픽 인스턴스(GUI)는 기타 원격 데이터 센터의 컴퓨팅 인스턴스를 표시하지 않습니다. 그러나 GUI에는 동일한 도시 내의 기타 데이터 센터(예: DALxx와 같이 이름이 첫 세 문자를 공유하는 데이터 센터)의 컴퓨팅 인스턴스가 포함됩니다. API 인터페이스를 사용하여 원격 데이터 센터에서 컴퓨팅 인스턴스를 추가할 수 있습니다.

## SSL 오프로드를 사용하여 지원되는 TLS 버전은 무엇입니까?
{:faq}

Cloud Load Balancer Service는 TLS 1.2 및 SSL 종료를 지원합니다.

다음은 지원되는 암호에 대한 목록 세부사항입니다(우선순위에 따라 나열됨).  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## 내 계정으로 작성할 수 있는 최대 로드 밸런서 서비스 인스턴스는 몇 개입니까?
{:faq}

현재 최대 50개의 서비스 인스턴스를 작성할 수 있습니다. 인스턴스가 추가로 필요하면 IBM 지원 센터에 문의하십시오. 

## IBM Cloud Load Balancer Service를 VMWare에서 사용할 수 있습니까?
{:faq}

SoftLayer 이동식 사설 주소가 지정된 VMWare 가상 머신은 로드 밸런서에 대한 백엔드 서버로서 지정될 수 있습니다. 이 기능은 현재 웹 UI(GUI)가 아닌 API를 통해서만 사용 가능합니다. SoftLayer에 의해 지정되지 않았으므로, API를 사용하여 추가된 이동식 사설 IP는 GUI에서 "알 수 없음"으로 표시됩니다. 이러한 종류의 구성은 Xen 및 KVM 등의 기타 하이퍼바이저와 함께 사용될 수 있습니다.

VMWare 가상 머신 지정 비-SoftLayer 주소(예: VMWare NSX 네트워크)는 로드 밸런서에 백엔드 서버로서 직접 추가될 수 없습니다. 그러나 구성에 따라서는 로드 밸런서에 대한 백엔드 서버로서 SoftLayer 사설 주소를 보유한 중개자(예: NSX 게이트웨이)를 구성할 수 있습니다(실제 서버는 VMware NSX에서 관리하는 네트워크에 연결된 VM임).

## 내 계정 아래의 공용 VLAN을 사용하여 로드 밸런서를 배치하기로 선택하였으며 내 공용 VLAN에 배치된 방화벽이 있는 경우, 방화벽이 로드 밸런서 서비스와 함께 작업하기 위해 필요한 구성은 무엇입니까?
{:faq}

TCP 포트 56501은 관리에 사용됩니다. 애플리케이션의 포트는 물론 이 포트에 대한 트래픽을 방화벽이 차단하지 않는지 확인하십시오. 차단하는 경우에는 로드 밸런서 프로비저닝에 실패합니다.

## 내 Softlayer 계정을 IBM Cloud에 연결한 후 기존 로드 밸런서의 모니터링 메트릭을 볼 수 없는 경우에는 어떻게 해야 합니까? 
{:faq}

계정을 연결한 후에는 기존 로드 밸런서에 대한 모니터링 메트릭을 사용할 수 없습니다. 로드 밸런서를 재작성하거나 지원 센터에 문의해야 합니다. 새로 작성된 로드 밸런서에 대한 모니터링 메트릭은 사용 가능합니다.

## 로드 밸런서 IP 주소가 고정되어 있습니까?
{:faq}

서비스에 기본 제공되는 탄력성으로 인해 로드 밸런서 IP 주소가 일정하게 유지되는지 보장할 수 없습니다. 확장되거나 축소되면 인스턴스의 FQDN과 연관된 사용 가능한 IP의 변경사항이 표시됩니다.

**참고:** 캐시된 IP 주소가 아니라 FQDN을 사용해야 합니다.

## 내 사설 VLAN에 배치된 방화벽이 있는 경우 방화벽이 내 로드 밸런서 서비스와 함께 작동하는 데 필요한 구성은 무엇입니까?
{:faq}

방화벽을 통한 IP 주소 허용에 대한 정보는 [IBM Cloud IP 범위](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges) 주제를 참조하십시오.

## UI에서 내 계층 7 구성을 볼 수 없는 이유는 무엇입니까?
{:faq}

현재 계층 7 지원은 공용 API를 통해서만 사용 가능하지만 곧 UI에서 이 기능을 사용할 수 있습니다. 자세한 정보는 [API 문서](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-api-reference)의 계층 7 섹션을 참조하십시오.

## 지원 티켓을 제출하는 데 필요한 정보는 무엇입니까?
{:faq}

지원 티켓을 제출하려면 제품 이름("IBM Cloud 로드 밸런서"), 로드 밸런서의 UUID(가능한 경우) 및 Softlayer 계정 번호를 제공하십시오. 지정된 로드 밸런서의 개요 페이지로 이동한 후 URL에서 UUID를 찾을 수 있습니다.
