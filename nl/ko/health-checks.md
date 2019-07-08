---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: health check, http, tcp, ports

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# IBM Cloud Load Balancer로 상태 검사 수행
{: #performing-health-checks-with-ibm-cloud-load-balancer}

상태 검사 정의는 각 백엔드 애플리케이션에 필수입니다. 상태 검사 구성의 포트 및 프로토콜은 정의된 백엔드 포트 및 프로토콜과 일치해야 합니다. 그렇지 않으면 구성이 거부됩니다.

로드 밸런서는 주기적인 상태 검사를 실행하여 백엔드 포트의 상태를 모니터링하고 이 상태에 따라 백엔드 포트에 클라이언트 트래픽을 전달합니다. 제공된 백엔드 서버 포트의 상태가 양호하지 않으면 이 백엔드 서버 포트에 새 연결을 전달하지 않습니다. 로드 밸런서는 양호하지 않은 포트의 상태를 계속 모니터링하고 연속 두 번의 상태 검사에 통과한 경우 사용을 재개합니다.

HTTP，HTTPS 및 TCP 포트에 대한 상태 검사는 다음과 같이 실행됩니다. 

* **HTTP:** 사전 지정된 URL에 대한 `HTTP GET` 요청은 백엔드 서버 포트로 전송됩니다. 서버 포트가 `200 OK` 메시지를 수신하면 상태가 양호하다고 표시됩니다. 기본 `GET` URL은 GUI를 사용한 “/”이고 이를 사용자 정의할 수 없습니다.

* **HTTPS:** 백엔드 암호화가 사용으로 설정되고 백엔드 프로토콜이 HTTPS로 설정된 경우에만 적용 가능합니다. 모든 상태 검사 메시지가 SSL로 암호화되는 점을 제외하고 메커니즘은 **HTTP**와 동일합니다. 백엔드 암호화에 대한 자세한 정보는 /docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-setting-backend-encryption을 참조하십시오. 

* **TCP:** 로드 밸런서는 지정된 TCP 포트에서 백엔드 서버를 사용하여 TCP 연결의 열기를 시도합니다. 연결 시도가 성공적이면 서버 포트는 상태가 양호하다고 표시되고 그런 다음 연결이 끊어집니다.

	기본 상태 검사 간격은 5초이고 상태 검사 요청에 대한 기본 제한시간은 2초이며 기본 재시도 횟수는 2회입니다.
  {: note}
