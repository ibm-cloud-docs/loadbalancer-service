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

# 오류 메시지 문제점 해결
{: #error-message-troubleshooting}

이 주제에서는 {{site.data.keyword.loadbalancer_full}}의 인스턴스를 작성/업데이트하는 동안 발생할 수 있는 일반적인 오류 메시지에 대한 정보를 제공합니다.

|오류 |설명  |솔루션  |
| ------------- | ------------- | ----- |
|`The maximum number of load balancers `n` has been reached.`|계정당 50개의 로드 밸런서 인스턴스만 허용됩니다. |계정당 50개 이하의 로드 밸런서 인스턴스가 있는지 확인하십시오. |
|`The maximum number of given protocols `n` in load balancer product order has been reached.` |로드 밸런서를 프로비저닝하는 동안 두 개의 프로토콜만 추가할 수 있습니다.  |더 많은 프로토콜이 필요한 경우 프로비저닝한 후 로드 밸런서 관리 플로우의 **프로토콜** 탭에서 최대 10개를 추가할 수 있습니다. 자세한 정보는 [서비스 모니터링 및 관리](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)를 참조하십시오. |
|`The maximum number of given server instances `n` in load balancer product order has been reached.` |로드 밸런서를 프로비저닝하는 동안 10개의 서버만 추가할 수 있습니다. |추가 서버가 필요한 경우 프로비저닝한 후 로드 밸런서 관리 플로우의 **서버 인스턴스** 탭에서 최대 50개를 추가할 수 있습니다. 자세한 정보는 [서비스 모니터링 및 관리](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)를 참조하십시오. |
|`Load balancer name must be a string and have at least 1 and up to 40 characters.` |로드 밸런서 이름은 필수입니다. 이름에는 영숫자 문자(또는 특수 문자 '-' 및 '.')만 사용하십시오. 이름은 특수 문자로 시작하거나 끝날 수 없으며 40자 길이로 제한되어야 합니다. |고유한 로드 밸런서 이름을 입력하십시오 (예: "ui-servers" 또는 "backend-servers").|
|`Format error found in given load balancer name.` |로드 밸런서 이름은 필수입니다. 이름에는 영숫자 문자(또는 특수 문자 '-' 및 '.')만 사용하십시오. 이름은 특수 문자로 시작하거나 끝날 수 없으며 40자 길이로 제한되어야 합니다. |고유한 로드 밸런서 이름을 입력하십시오 (예: "ui-servers" 또는 "backend-servers").|
| `Load balancer with the same name (case insensitive) already exists.` |동일한 이름의 로드 밸런서가 있습니다. |계속하려면 고유 로드 밸런서 이름을 입력하십시오(예: "ui-servers" 또는 "backend-servers"). |
| `Load balancer description must be a string and not exceed 255 characters.` | 로드 밸런서 설명은 문자열이고 255자를 초과하지 않아야 합니다. | 설명을 255자로 제한하십시오. |
| `Frontend port 80 is already used.` | 이미 사용 중인 프론트 엔드 포트를 입력했을 수 있습니다. | 고유한 프론트 엔드 포트를 입력하십시오. |
| `Backend port must be an integer.` | 올바르지 않은 백엔드 포트 값을 입력했을 수 있습니다. | 1 - 65535의 백엔드 포트 번호를 입력하십시오. |
| `Since the protocol and port are not editable in health monitor, this error is impossible from UI.`| 사설 서브넷은 표준 유형이 아니므로 로드 밸런서를 작성하는 데 사용할 수 없습니다. | IBM 지원 센터에 문의하십시오. |
| `Private subnet `xyz` must have at least `n` free IP addresses.` | 선택한 사설 서브넷에 사용 가능한 IP 주소가 없습니다. | 자세한 정보는 해당 [문제점 해결 단계](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting)를 참조하십시오. |
| `Specified private subnet VLAN is on router `xyz`. 그러나 동일한 라우터에서 `n`개의 사용 가능한 IP가 있는 공용 VLAN을 찾을 수 없습니다.` | 이 문제는 프로비저닝 중에 **이 계정의 공인 서브넷에서 할당** 옵션을 선택했기 때문에 발생합니다. | 대신 **IBM 시스템 풀에서 할당** 옵션을 선택하거나 IBM 지원 센터에 문의하십시오.|
| `Specified private subnet VLAN is on router `xyz`. 그러나 동일한 라우터에서 VLAN을 포함하는 `n`개의 사용 가능한 IP가 있는 공인 서브넷을 찾을 수 없습니다.` | 이 문제는 프로비저닝 중에 **이 계정의 공인 서브넷에서 할당** 옵션을 선택했기 때문에 발생합니다. | 대신 **IBM 시스템 풀에서 할당** 옵션을 선택하거나 IBM 지원 센터에 문의하십시오.|
| `Given new description must be a string.`| 올바르지 않은 설명을 입력했을 수 있습니다. | 255자 이하의 올바른 로드 밸런서 설명을 입력하십시오. |
| `A billing item is required to process a cancellation for load balancer uuid=aaaa-bbbb-cccc-dddd.` | 계정의 비용 청구 정보가 누락되었거나 올바르지 않습니다. 로드 밸런서는 취소할 수 없습니다. | IBM 지원 센터에 문의하십시오.|
| `An internal error occurred. 데이터를 검색할 수 없습니다.` | 메트릭 데이터를 검색할 수 없습니다. | 페이지를 다시 로드하십시오. 문제가 지속되면 IBM 지원 센터에 문의하십시오. |
| `Front-end port must be an integer between 1 and 65535 excluding the range 56500-56520.` | 56500-56520의 프론트 엔드 포트 번호를 입력했을 수 있습니다. | 1 - 65535의 고유한 포트 번호를 입력하십시오. 단, 56500 - 56520 범위는 제외하십시오. |
| `Back-end port must be an integer.` | 올바르지 않은 백엔드 포트 값을 입력했을 수 있습니다. | 1 - 65535의 백엔드 포트 번호를 입력하십시오. |
| `Back-end port must be an integer between 1 and 65535 excluding the range 56500-56520.` | 56500 - 56520 사이의 백엔드 포트를 입력했을 수 있습니다.| 1 - 65535의 백엔드 포트 번호를 입력하십시오. 단, 56500 - 56520 범위는 제외하십시오. |
| `Backend protocol HTTP is not compatible with frontend protocol TCP.` | 호환되지 않는 백엔드 프로토콜과 프론트 엔드 프로토콜 조합을 선택했을 수 있습니다. | 다음 형식의 올바른 프론트 엔드와 백엔드 프로토콜 조합을 선택하십시오. `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Member weight <some value> is provided for member abcd-xxxx-yyyy-2222. The allowed weight value is 0-100 `| 올바르지 않은 가중치를 입력했을 수 있습니다. | 0 - 100의 가중치 값을 입력하십시오. |
| `There was a problem fetching the servers.` | 네트워크 제한시간 문제 때문에 발생할 수 있습니다. | 페이지를 다시 로드하십시오. 문제가 지속되면 IBM 지원 센터에 문의하십시오.|
