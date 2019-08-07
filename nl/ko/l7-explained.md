---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policies, rules, pools

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

# 계층 7 로드 밸런싱
{: #layer-7-load-balancing}

{{site.data.keyword.loadbalancer_full}} Service는 계층 7(애플리케이션 계층) 데이터를 사용하여 Bare Metal 및 Virtual Server 인스턴스를 포함한 다중 서버 인스턴스 간에 트래픽을 분배합니다.

 * 분배될 데이터 트래픽은 정책 및 규칙을 사용하여 분류됩니다.
 * 정책은 데이터 트래픽이 정책과 연관된 모든 규칙과 일치하는 경우 수행할 조치를 정의합니다.
 * 계층 7(L7) 로드 밸런싱은 HTTP 및 HTTPS 트래픽에 대해서만 지원됩니다.

## 계층 7 정책 및 규칙
{: #layer-7-policies-and-rules}
계층 7 정책은 프론트 엔드 애플리케이션 포트와 연관됩니다. 다중 정책이 프론트 엔드 포트와 연관될 수 있습니다.

 * 이러한 정책은 각 정책에 지정된 우선순위에 따라 순서대로 평가됩니다.
 * 정책이 일치되면 연관된 조치가 수행됩니다.
 * 각 L7 규칙은 정책과 연관됩니다.
 * 정책과 연관된 모든 규칙이 `true`로 평가되면 정책이 일치되므로 연관된 조치가 수행됩니다.

추가 세부사항은 [L7 정책 및 규칙](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy)을 참조하십시오.

## 계층 7 풀
{: #layer-7-pools}
각 계층 7 로드 밸런서 풀에는 하나 이상의 논리 서버 인스턴스가 포함됩니다.

 * 각 논리 서버 인스턴스는 IP 주소 및 포트 번호로 식별됩니다.
 * 각 풀에는 연관된 상태 모니터가 있습니다. 상태 모니터는 풀에 있는 모든 서버의 상태를 모니터합니다.
 * 세션 지속성을 위해 풀을 구성할 수 있습니다.
 * 세션 지속성을 구성하려면 클라이언트의 소스 IP 주소를 사용하십시오.

추가 세부사항은 [L7 풀](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool)을 참조하십시오.
