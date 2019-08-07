---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# 데이터 로깅
{: #data-logging}

데이터 및 상태 검사 로그는 디버깅 및 유지보수를 위해 중요합니다. 데이터 로깅 기능이 사용으로 설정되면 IBM 로드 밸런서가 이 로그를 사용자 계정의 [IBM Cloud 로그 분석 서비스![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://logging.ng.bluemix.net){:new_window}에 전달합니다. 

다음을 수행하여 이 기능을 사용 또는 사용 안함으로 설정할 수 있습니다. 

* 새 로드 밸런서 작성 및 이 기능을 켜짐으로 설정
* API `enableOrDisableDataLogs` 사용

## IBM Cloud 로깅 분석 서비스에서 로그 보기
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

고객의 IBM Cloud 계정으로 [IBM Cloud 로깅 분석 서비스![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://logging.ng.bluemix.net){:new_window}에 로그인하십시오. Kibana에서 로그를 볼 수 있습니다. 자세한 정보는 [이 주제](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana)를 참조하십시오.

Softlayer 및 IBM Cloud 계정이 연결되어 있는 경우에만 데이터 로그가 전송됩니다. Softlayer 계정과 연관된 IBM Cloud 계정을 선택한 후 Kibana 대시보드에 로그인하십시오.
{: tip}

## 로그 출력 예
{: #log-output-examples}

다음 출력은 {{site.data.keyword.loadbalancer_full}} 데이터 로그의 예입니다. 

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576`은 로드 밸런서 이름이고 `dal09`는 데이터 센터입니다. 
* `323698`은 계정 ID입니다. `643866`은 로드 밸런서 ID입니다. `713576`은 멤버 ID입니다. 
* `xxx.xxx.xxx.xxx`는 GDPR을 위해 마스크된 공인 IP입니다. 

다음 출력은 IBM Cloud 로깅 분석 서비스 내의 상태 검사 로그 예입니다. 

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23`은 멤버 IP 주소입니다. 
* `682175`는 멤버 ID입니다. 
