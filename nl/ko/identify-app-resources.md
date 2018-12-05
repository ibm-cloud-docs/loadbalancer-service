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

# 애플리케이션 서버 리소스 식별
맨 아래에 있는 표에서 **서버 인스턴스**를 찾은 다음 **+**를 클릭하여 로드 밸런서 뒤에 추가하십시오. 계정에 있는 IBM Cloud VSI(Virtual Server Instance) 및 Bare Metal Server 중에서 선택할 수 있습니다.

이러한 서버 인스턴스는 로드 밸런서 서비스를 배치하는 데이터 센터에 로컬이어야 합니다. 또한 동일한 도시 내의 인접 데이터 센터의 서버 인스턴스를 추가할 수도 있습니다(예를 들어, 데이터 센터 이름의 처음 3개 문자가 동일한 경우).

<img src="images/locate-server-instance.png" alt="그림" style="width: 300px;"/>

**다음**을 클릭하십시오.

**참고:** 

1. 서버 **가중치**는 **가중치 라운드 로빈** 로드 밸런싱 메소드를 사용 중인 경우에만 관련됩니다. 기본 가중치는 50이고 범위는 0 - 100입니다. 다른 로드 밸런싱 메소드를 사용하는 경우 가중치가 흐리게 표시됩니다.
2. 최대 애플리케이션 서버 수 한계에 대한 자세한 정보는 [애플리케이션 서버 수에 대한 제한사항](faqs.html#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-)을 참조하십시오.

## 다음에 수행할 작업
주문하기 전에 주문의 [컨텐츠를 검토](order-lb.html)하십시오.
