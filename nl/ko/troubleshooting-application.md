---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, problem, server, application

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

# 애플리케이션 서버 문제점 해결
{: #application-server-troubleshooting}

이 주제에서는 로드 밸런서를 사용하는 동안 발생할 수 있는 일반적인 문제에 대한 정보를 제공합니다.

## 백엔드 서버가 비정상임
{: #the-back-end-server-is-unhealthy}
백엔드 서버의 상태가 실패이면 다음 목록을 확인하여 수정하십시오.

* 구성된 백엔드 프로토콜의 포트가 애플리케이션이 청취 중인 포트와 일치합니까?
* 구성된 상태 검사에 올바른 프로토콜(TCP 또는 HTTP), 포트 및 URL(HTTP의 경우) 정보가 있습니까? HTTP의 경우 애플리케이션이 구성된 상태 검사 URL에 대해 `200 OK`로 응답하는지 확인하십시오.
* 백엔드 서버가 로드 밸런서와 다른 서브넷에 있습니까? 그렇지 않은 경우 VLAN Spanning이 사용으로 설정되었는지 확인하십시오.
* 백엔드 서버가 사용으로 설정된 보안 그룹이 있는 Virtual Server입니까? 그렇다면 보안 그룹 규칙이 로드 밸런서와 Virtual Server 간의 트래픽을 허용하는지 확인하십시오.
