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

# 서비스 모니터링 및 관리
로드 밸런서 요약 페이지에서 서비스 이름 URL을 클릭하여 구성을 편집하거나 서비스 성능을 모니터할 수 있습니다. 

로드 밸런서 서비스 인스턴스의 **완전한 도메인 이름(FQDN) 주소**가 서비스 이름 바로 아래에 표시될 수 있습니다. 일반 사용자가 이 FQDN 주소를 통해 애플리케이션에 연결할 수 있습니다. 로드 밸런서 서비스의 공인 및 사설 IP 주소는 외부에 노출되지 않고 FQDN 주소만 노출됩니다. 

<img src="images/fqdn-address.png" alt="그림" style="width: 300px;"/>

**개요** 탭에서는 서비스의 상위 레벨 상태 정보를 제공합니다. 애플리케이션 서버와 해당 포트의 현재 상태를 표시합니다. 또한 처리량, 연결 속도, 동시 연결 수와 같은 시스템 성능의 빠른 요약을 제공합니다. 

시스템 성능의 실시간 차트를 보려면 **모니터링** 탭으로 이동하십시오. 다양한 지속 기간 동안 개별 애플리케이션 포트별로 이러한 그래프를 볼 수 있습니다. 

<img src="images/monitor-lb.png" alt="그림" style="width: 300px;"/>

**프로토콜**, **서버 인스턴스** 및 **상태 검사** 탭으로 이동하여 기본 구성을 편집할 수 있습니다. 예를 들어, 추가 애플리케이션 포트를 정의하거나 SSL 암호 목록을 사용자 정의하려면 프로토콜 탭으로 이동하십시오. 

<img src="images/protocols-monitor.png" alt="그림" style="width: 300px;"/>
