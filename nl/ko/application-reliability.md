---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud Internet Services에서 글로벌 로드 밸런싱으로 애플리케이션 안정성 및 확장성 개선
e-commerce 웹 사이트를 보유하고 있으며 일반 사용자가 언제든지 액세스할 수 있어야 하는 애플리케이션을 호스팅 중인 경우에는 애플리케이션의 24*7(일주일에 7일, 하루 24시간 내내) 가용성과 성능에 관심이 있을 수 있습니다. 

IBM Cloud Internet Services에서 사용 가능한 글로벌 로드 밸런싱 기능을 사용하면 최상의 가능한 일반 사용자 환경을 제공하면서도 애플리케이션의 안정성과 확장성을 개선하는 데 도움이 될 수 있습니다. 이 안내서는 글로벌 로드 밸런싱 구성에 대한 검토사항을 제공합니다.  

## 수행할 내용

이 단계별 학습서에서는 아래에 예시된 것과 유사한 설정을 구성하는 방법에 대해 학습합니다.

<img src="images/Reliability1.png" alt="그림" style="width: 300px;"/>

이 예에서 애플리케이션 리소스는 두 개의 데이터 센터 위치에 배치됩니다. 하나는 미국 서부이고 다른 하나는 미국 동부 해안입니다. 일반 사용자는 세계 각국에서 이 애플리케이션에 액세스할 수 있습니다. 

태스크  |설명
------------- | -------------
[CIS 인스턴스 작성](create-cis.html) |IBM 고객 포털을 사용하여
IBM Cloud Internet Services 인스턴스 작성을 시작합니다.
[도메인 관련 정보 입력](input-domain.html) | 보안 및 글로벌 로드 밸런싱이 제공될 도메인에 대한 정보를 입력합니다.
[글로벌 로드 밸런서 구성 시작](begin-config.html) | 글로벌 로드 밸런서 구성을 시작합니다.
[애플리케이션 리소스 식별](identify-app-resources.html) | 상태 검사 메커니즘 및 오리진 풀 등의 애플리케이션 리소스를 식별합니다.
[글로벌 로드 밸런서 정의](define-global-lb.html) | 호스트 이름을 지정하고 오리진 풀을 추가 및 조정하며 트래픽이 클라이언트에 제공되는 방법을 제어하는 규칙을 추가로 정의하여 글로벌 로드 밸런서 구성을 정의합니다.
