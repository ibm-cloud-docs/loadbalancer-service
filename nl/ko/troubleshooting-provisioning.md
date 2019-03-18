---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 로드 밸런서 프로비저닝 문제점 해결
{: #load-balancer-provisioning-troubleshooting}

이 주제에서는 IBM© Cloud Load Balancer의 새 인스턴스를 작성하는 동안 발생할 수 있는 일반적인 문제에 대한 정보를 제공합니다.

## 서브넷에 IP 주소가 충분하지 않음
IBM Cloud 로드 밸런서에는 사설 서브넷의 두 개 이상의 사용 가능한 IP 주소가 필요합니다. 또한 로드 밸런서가 공용 로드 밸런서이고 **IBM 시스템 풀** 옵션이 사용되지 않으면 공인 서브넷에서도 두 개 이상의 사용 가능한 IP 주소가 필요합니다. 

아래 단계에 따라 서브넷에 사용 가능한 IP가 있는지 확인하십시오.

1. [고객 포털 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://control.softlayer.com){:new_window}로 이동하고 **네트워크 > IP 관리 > 서브넷**을 선택하여 서브넷 섹션으로 이동하십시오.

2. 사용 가능한 IP가 있는지 확인하려는 서브넷을 클릭하십시오.

	<img src="images/subnet_list.png" alt="그림" style="width: 600px;"/>
		
3. 선택한 서브넷에 대한 세부사항 페이지에 해당 서브넷에 있는 모든 IP의 상태가 표시됩니다.

## 공용 및 사설 VLAN의 방화벽에 대한 문제
방화벽을 통한 IP 주소 허용에 대한 정보는 [IBM Cloud IP 범위](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges) 주제를 참조하십시오.
 
## 로드 밸런서 오류 메시지 보기
로드 밸런서의 오류 메시지를 보려면 다음 프로시저를 수행하십시오.

1. 목록 페이지에서 로드 밸런서를 클릭하여 해당 세부사항을 보십시오. 
2. 로드 밸런서의 상태 옆에 있는 오류 기호 위로 마우스를 이동하십시오.

<img src="images/lbaas_error_message.png" alt="그림" style="width: 500px;"/>

로드 밸런서가 `ERROR` 상태이면 복구할 수 없으며 삭제해야 합니다.
