---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 시작하기
IBM Cloud 로드 밸런서의 사용을 시작하려면 두 가지 기본 항목이 필요합니다.

* IBM 계정: [IBM ID ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/account/us-en/signup/register.html)
* IBM 서버: [Bare Metal](/docs/bare-metal/about.html#getting-started-with-bare-metal-servers) 또는 [VSI(Virtual Server Instance)](/docs/vsi/vsi_index.html#getting-started-with-virtual-servers)

**IBM ID** 계정을 받을 때 도움이 필요하면 [IBM 영업 담당자 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud-computing/bluemix/contact-us)에게 문의하여 추가 안내를 받으십시오.

기존 IBM Cloud 인프라(SoftLayer) 계정이 있는 경우에는 IBM ID와 [사용자 계정을 연결 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/account/softlayerlink.html#link_user_account)할 수 있습니다.

## 로드 밸런서 주문

IBM Cloud Load Balancers Service를 주문하려면 [IBM Cloud 카탈로그](https://console.bluemix.net/catalog/infrastructure/load-balancer-group)에서 **네트워크 > Load Balancers > IBM Cloud IBM Cloud Load Balancer**를 선택하십시오. 로그인하거나 새 계정을 작성한 후에 다음 프로시저를 수행하십시오.

1. 데이터 센터를 선택하고 서비스 플랜을 검토하십시오. **다음**을 클릭하십시오.
2. 로드 밸런서를 배치할 서브넷을 선택하십시오. 로드 밸런서 서비스 인스턴스는 이 서브넷의 네트워크 인터페이스 중 하나를 보유하게 됩니다. 애플리케이션 서버가 이 서브넷에 있는지 아니면 이 서브넷에서 접근할 수 있는지 확인하십시오. 필요한 경우 VLAN Spanning을 사용하십시오. **다음**을 클릭하십시오.
3. 기본 서비스 매개변수를 정의하십시오(예: 이름, 설명, 프론트 엔드 및 백엔드 애플리케이션 프로토콜/포트, 로드 밸런싱 메소드). 

	초기 서비스 작성 중에 최대 두 개의 프로토콜을 정의할 수 있습니다. 서비스가 작성된 후에는 최대 열 개의 프로토콜을 정의할 수 있습니다. 고유한 프론트 엔드 포트도 사용해야 합니다. 
	
	완료되면 **다음**을 클릭하십시오.
	
4. 필요한 경우 상태 점검 매개변수를 조정하십시오. 그렇지 않으면 기본 설정을 사용하십시오. **다음**을 클릭하십시오.
5. 로드 밸런서 뒤에 하나 이상의 서버 인스턴스를 연관시키십시오. 데이터 센터에 로컬인 서버 인스턴스만 표시됩니다. **다음**을 클릭하십시오.
6. 요약 페이지를 검토한 후 **작성**을 클릭하십시오.

	요약 페이지에는 방금 전에 작성한 로드 밸런서 서비스 인스턴스가 표시됩니다. **상태** 필드를 참조하십시오. `Offline` 상태는 로드 밸런서가 서비스 중이 아님을 의미합니다. 해당 상태가 `Online`으로 변경되어야만 새 구성을 작성할 수 있고 로드 밸런싱 서비스를 제공할 수 있습니다. 현재 상태를 보려면 화면을 새로 고쳐야 할 수 있습니다.

	이 페이지에서 서비스 이름을 클릭하면 서비스 개요 페이지로 이동합니다. **프로토콜**, **상태 검사** 및 **서버 인스턴스** 탭으로 이동하여 구성을 추가로 편집할 수 있습니다.

단계별 구성 지침은 [탄력적인 서버 로드 밸런싱을 위해 IBM Cloud 로드 밸런서를 작성하고 사용하는 방법](reliability-guide.html)을 참조하십시오.
