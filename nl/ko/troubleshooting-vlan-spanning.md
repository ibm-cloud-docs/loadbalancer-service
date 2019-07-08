---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: vlan, troubleshooting, problems, questions

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

# 로드 밸런서 VLAN Spanning 문제점 해결
{: #load-balancer-vlan-spanning-troubleshooting}

이 주제에서는 로드 밸런서 및 로드 밸런서에 연결된 컴퓨팅 인스턴스가 다른 서브넷에 있는 경우에 발생할 수 있는 일반적인 문제에 대한 정보를 제공합니다. 로드 밸런서가 다른 서브넷에 있는 컴퓨터 인스턴스와 통신하고 요청을 전달하려면 로드 밸런서에 대한 VLAN Spanning이 사용으로 설정되어야 합니다.

1. [고객 포털 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://control.softlayer.com){:new_window}에 로그인하고 **네트워크 > IP 관리**로 이동한 다음 **VLAN**을 클릭하십시오.

2. **VLAN Spanning**을 **설정**으로 전환하십시오.

<img src="images/vlan-spanning.png" alt="그림" style="width: 500px;"/>

이렇게 하면 로드 밸런서와 해당 컴퓨팅 인스턴스 간의 통신이 열립니다.
