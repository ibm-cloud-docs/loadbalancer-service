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

# IBM Cloud 로드 밸런서 작성
IBM Cloud 로드 밸런서 서비스를 작성하려면 다음 프로시저를 수행하십시오.

1. 브라우저에서 [고객 포털 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://control.softlayer.com/){: new_window}을 열고 사용자 계정에 로그인하십시오.

2. **카탈로그**를 클릭한 후 인프라 섹션에서 **네트워크 > 로드 밸런서**로 이동하십시오.

	<img src="images/catalog-load-balancer.png" alt="그림" style="width: 600px;"/>

3. **IBM Cloud 로드 밸런서**(기본 선택사항)를 선택하고 **작성**을 클릭하십시오. 

	**작성** 대신에 **업그레이드**가 표시되면 [이러한 단계 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/account/softlayerlink.html#link_customer_accounts)에 따라 IBM Cloud 인프라(Softlayer) 계정을 연결해야 합니다.

	<img src="images/create-load-balancer.png" alt="그림" style="width: 600px;"/>

4. **데이터 센터** 드롭 다운에서 선호하는 데이터 센터를 선택하고 정보를 검토한 후 **다음**을 클릭하십시오.

	<img src="images/select-datacenter.png" alt="그림" style="width: 600px;"/>

5. 로드 밸런서 유형을 지정하십시오.

	공용 인터넷에 액세스해야 하는 인터넷 연결 애플리케이션의 경우 **공용(인터넷 연결)**을 선택하십시오.

	<img src="images/select-lb-type.png" alt="그림" style="width: 600px;"/>
	
	기본적으로 공용 로드 밸런서는 IBM 글로벌 주소 풀에서 글로벌로 고유한 공인 IP 주소를 수신합니다. 그러나 사용자 고유의 주소 풀에서 공용 주소를 지정하거나 계정 내의 방화벽 서비스 뒤에 배치하려면 공인 서브넷에 [충분한 IP 주소](troubleshooting-provisioning.html)가 있는지 확인하고 **사용자 계정의 공인 서브넷에서 할당**을 선택하십시오.

	공용 인터넷에 액세스할 필요가 없는 내부 전용 애플리케이션의 경우 **내부(사설)** 유형을 선택하십시오.

	<img src="images/lb-type-private.png" alt="그림" style="width: 500px;"/>

	인터넷 연결 및 내부 로드 밸런서 유형 모두의 경우 로드 밸런서를 배치할 계정 내의 사설 서브넷 중 하나를 선택하십시오. 이 서브넷에서 애플리케이션 서버에 접속할 수 있어야 합니다. 필요한 경우 적절한 네트워크 연결이 가능하도록 VLAN Spanning을 사용으로 설정하십시오.

	사설 서브넷이 표시되지 않는 경우 **이전**을 클릭한 후 사설 서브넷이 있는 다른 데이터 센터를 선택하십시오.

6. **다음**을 클릭하여 구성을 완료하십시오.

## 다음에 수행할 작업
[기본 매개변수](begin-lb-config.html)로 로드 밸런서를 구성하십시오.
