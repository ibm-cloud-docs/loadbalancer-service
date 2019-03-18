---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


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

# IBM Cloud Load Balancer 매개변수 구성
{: #configuring-ibm-cloud-load-balancer-parameters}

로드 밸런서를 작성한 후 탄력적인 로드 밸런싱을 사용하도록 구성할 수 있습니다. 이를 위해서는 다음을 수행하십시오.

1. 로드 밸런서의 이름을 지정하고 선택적으로 설명을 추가하십시오.

	<img src="images/lb-config-basic.png" alt="그림" style="width: 300px;"/>

2. 애플리케이션이 청취 중인 프로토콜 및 포트를 식별하여 애플리케이션 프로파일의 세부사항을 입력하십시오. 프론트 엔드 및 백엔드 둘 다에 동일한 구성을 사용하거나 다른 프론트 엔드 포트를 노출할 수 있습니다(예를 들어, 보안을 위해).

3. 기본 로드 밸런싱 메소드는 **라운드 로빈**입니다. 애플리케이션 요구사항에 따라 드롭 다운 목록에서 **가중치 라운드 로빈** 및 **최소 연결**로 변경할 수 있습니다.

4. 선택적으로 **세션 고정성**을 사용으로 설정할 수 있습니다. 사용으로 설정되면 지정된 일반 사용자의 모든 요청(예: 소스 IP가 동일한 요청)이 시스템 정의 "고정" 시간 동안 동일한 백엔드 서버로 이동합니다.

5. 애플리케이션에 대한 **최대 연결 한계**를 설정할 수도 있습니다.

6. 애플리케이션이 청취 중일 수 있는 추가 포트 및 프로토콜을 지정하려면 **프로토콜 추가**를 클릭하십시오. 모든 프론트 엔드 포트가 고유해야 합니다. HTTP, HTTPS 또는 TCP를 프론트 엔드 프로토콜로 선택할 수 있습니다.

	<img src="images/lb-add-protocol.png" alt="그림" style="width: 300px;"/>

	초기 구성 시 최대 두 개의 포트를 정의할 수 있습니다. 서비스 인스턴스를 작성한 후 포트를 더 추가할 수 있습니다. 허용되는 최대 포트 수에 대한 자세한 정보는 [포트 수에 대한 제한사항](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-)을 참조하십시오.
{:note:}

7. IBM Cloud 로드 밸런서는 수신 HTTPS(HTTP over SSL) 연결을 종료하고 일반 텍스트 HTTP로 백엔드 애플리케이션 서버와 통신하며 백엔드 프로토콜을 HTTP로 선택하는 경우 서버에서 프로세서 집약적 SSL 태스크를 오프로드합니다. 선택한 백엔드 프로토콜이 HTTPS이면 로드 밸런서와 백엔드 서버 사이에 트래픽이 암호화됩니다. SSL 인증서를 업로드해야 합니다. 드롭 다운 목록에서 사용 가능한 인증서 중 하나를 선택하십시오.  

	<img src="images/lb-ssl-cert.png" alt="그림" style="width: 300px;"/>

	기존 인증서가 없는 경우 **새 인증서 추가**를 클릭하십시오. 그러면 새 인증서를 구매하거나 기존 인증서를 업로드할 수 있는 IBM Cloud 인증서 서비스로 이동합니다. 
	
	인증서를 추가한 후 로드 밸런서 구성 페이지로 돌아와서 SSL 인증서 드롭 다운 목록 아래의 새로 고치기 아이콘을 클릭하여 새로 업로드된 인증서를 보고 추가하십시오.

	<img src="images/order-ssl-cert.png" alt="그림" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="그림" style="width: 300px;"/>

	**참고: 기능에 문제가 발생할 수 있으므로 HTTPS 리스너와 연관된 인증서를 삭제하지 마십시오.**

8. **다음**을 클릭하십시오.

## 상태 검사 구성
각 애플리케이션 포트에 대한 상태 검사 정의는 필수입니다. 해당 포트는 이전 기본 구성 메뉴에서 식별된 백엔드 포트입니다.

<img src="images/config-health-check.png" alt="그림" style="width: 300px;"/>

시스템에서 이러한 백엔드 포트에 대한 기본 상태 검사 구성을 미리 채웁니다. 애플리케이션 요구사항에 맞게 이러한 설정을 사용자 정의할 수 있습니다.

* **간격**: 두 번의 연속 상태 검사 시도 사이의 간격(초)
* **제한시간**: 시스템에서 상태 검사 요청에 대한 응답을 기다리는 최대 시간
* **최대 시도 수**: 포트를 비정상으로 선언하기 전에 시스템에서 시도하는 최대 추가 상태 검사 횟수
* **경로**: 상태 검사를 위한 HTTP URL 경로     

**다음**을 클릭하여 선택사항을 사용으로 설정하십시오.

## 다음에 수행할 작업
오리진 풀 및 상태 검사 메커니즘과 같은 [애플리케이션의 리소스를 식별](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources)하십시오.
