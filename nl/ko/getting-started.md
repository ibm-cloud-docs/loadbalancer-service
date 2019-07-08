---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# IBM Cloud Load Balancer 시작하기
{: #getting-started}

IBM© Cloud 로드 밸런서의 사용을 시작하려면 두 가지 기본 항목이 필요합니다.

* IBM 계정: [IBM ID ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* IBM 서버: [Bare Metal](/docs/bare-metal?topic=bare-metal-about) 또는 [VSI(Virtual Server Instance)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

**IBM ID** 계정을 받을 때 도움이 필요하면 [IBM 영업 담당자 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window}에게 문의하여 추가 안내를 받으십시오.

기존 IBM Cloud Infrastructure(SoftLayer) 계정이 있으면 IBM ID와 [계정을 연결](/docs/account?topic=account-unifyingaccounts)할 수 있습니다.

## 로드 밸런서 주문
{: #ordering-a-load-balancer}

IBM Cloud Load Balancer 서비스를 주문하려면 [IBM Cloud 카탈로그![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}에서 **IBM Cloud Load Balancer**를 선택하십시오. 그런 다음 **작성**을 클릭한 후 다음 프로시저를 수행하십시오. 

1. 기본 서비스 매개변수를 정의하십시오(예: 이름 및 설명). 
2. 데이터 센터를 선택하십시오. 
3. 로드 밸런서 유형으로 **공용**을 선택하십시오. 
4. 로드 밸런서를 배치할 서브넷을 선택하십시오.

  로드 밸런서 서비스 인스턴스는 이 서브넷의 네트워크 인터페이스 중 하나를 보유하게 됩니다. 애플리케이션 서버가 이 서브넷에 있는지 아니면 이 서브넷에서 접근할 수 있는지 확인하십시오. 필요한 경우 VLAN Spanning을 사용하십시오.
  {: note}

5. 프론트 엔드 및 백엔드 애플리케이션 프로토콜 및 포트를 작성하십시오. 

  이 구성에 대한 자세한 정보는 [IBM Cloud Load Balancer 매개변수 구성](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters)을 참조하십시오.
  {: note}

6. SSL 오프로드를 사용으로 설정하려면 프론트 엔드 프로토콜을 HTTPS로 설정하고 백엔드 프로토콜을 HTTP로 설정하십시오. 그런 다음 인증서 드롭 다운 상자에서 SSL 인증서를 선택하십시오. 

  모든 기존 SSL 인증서는 [IBM Cloud 인증서 저장소![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}를 통해 관리됩니다. SSL 인증서가 없는 경우에는 여기서 작성할 수 있습니다. 

7. 필요한 경우 상태 점검 매개변수를 조정하십시오. 그렇지 않으면 기본 설정을 사용하십시오.

  상태 검사 매개변수에 대한 자세한 정보는 [IBM Cloud Load Balancer 매개변수](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks)를 참조하십시오.
  {: note}

8. **서버 연결**을 클릭하여 로드 밸런서 뒤에 하나 이상의 서버 인스턴스를 연관시키십시오. 데이터 센터에 로컬인 서버 인스턴스만 표시됩니다.
9. 페이지를 검토하고 서비스 계약을 확인한 후 **작성**을 클릭하십시오. 

모든 서비스 인스턴스를 보여주는 로드 밸런서 목록이 표시됩니다. 

이 페이지에서 서비스 이름을 클릭하면 서비스 개요 페이지로 이동합니다. **프로토콜**, **상태 검사** 및 **서버 인스턴스** 탭으로 이동하여 구성을 추가로 편집할 수 있습니다.

새로 작성된 로드 밸런서가 이 목록에 즉시 표시되지 않을 수 있습니다. 몇 분이 지나면 새 로드 밸런서가 회색(상태가 `Offline`임을 나타냄)으로 표시됩니다. 다시 몇 분이 지나면 새 로드 밸런서가 초록색(`Online` 상태임을 나타냄)으로 표시됩니다. 이러한 변경을 보기 위해 화면을 새로 고쳐야 할 수 있습니다.
{: note}

새 클라우드 로드 밸런서 구성에 대한 단계별 지침은 [탄력적인 서버 로드 밸런싱을 위해 IBM Cloud Load Balancer를 사용하는 방법](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing)을 참조하십시오. 
