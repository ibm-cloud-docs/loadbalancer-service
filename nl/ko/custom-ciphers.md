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

# HTTPS 애플리케이션에 대해 선호하는 암호 스위트 선택
IBM Cloud 로드 밸런서가 해당 HTTP 클라이언트와의 보안 연결을 형성하는 데 도움을 주는 암호 알고리즘입니다.

IBM에서는 로드 밸런서와 클라이언트 간의 통신을 보호하기 위해 선택할 수 있는 승인된 암호 스위트를 제공합니다.

기존 로드 밸런서에 대한 선호하는 암호 스위트를 선택하거나 새 로드 밸런서를 작성할 때 지정할 수 있습니다. 

## 기존 로드 밸런서에 대한 암호 선택
기존 로드 밸런서에 대한 암호 스위트 구성을 선택하려면 고객 포털에서 로드 밸런서 화면으로 이동하여 프로토콜 탭을 클릭하십시오. HTTPS가 프론트 엔드 프로토콜로 선택되지 않으면 암호 스위트 목록이 표시되지 않습니다.

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="그림" style="width: 700px;"/>
  
HTTPS를 프론트 엔드 프로토콜로 선택하면 사용 가능한 암호 스위트가 로드 밸런서 세부사항 아래에 표시됩니다. 

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="그림" style="width: 600px;"/>
  
암호 테이블은 편집 가능하며 SSL 핸드쉐이크를 위해 원하는 암호 스위트를 선택할 수 있습니다. **편집**을 선택하고 구현할 암호를 선택한 후 **저장**을 클릭하십시오.
  
**참고:** 지원되는 암호 목록은 [SSL 오프로드](ssl-offload.html)를 참조하십시오.

## 새 로드 밸런서 작성 시 암호 선택

새 로드 밸런서를 작성할 때 암호 스위트를 선택하려면 다음을 수행하십시오.

1. 지시사항에 따라 [로드 밸런서를 작성](create-load-balancer.html)하십시오.
  
2. 암호 스위트 구성은 HTTPS 프론트 엔드 프로토콜에만 적용 가능합니다. **프로토콜 추가** 섹션에 대한 구성 단계에 도달하면 **HTTPS 프로토콜**을 선택하십시오.

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="그림" style="width: 500px;"/>
  
3. 기본 암호 세트가 구성에서 이미 선택되어 있지만 로드 밸런서 구성을 완료한 후에만 편집할 수 있습니다. 
  
	주제의 지시사항에 따라 로드 밸런서 구성을 완료하십시오. 완료되면 **로드 밸런서 세부사항** 아래의 **프로토콜 탭**에서 기본 암호 목록을 볼 수 있습니다.

	<img src="images/View-CustomCiphers.png" alt="그림" style="width: 600px;"/>
  
4. 암호 테이블은 편집 가능하며 SSL 핸드쉐이크를 위해 원하는 암호 스위트를 선택할 수 있습니다. **편집**을 선택하고 구현할 암호를 선택한 후 **저장**을 클릭하십시오.
	
	**참고:** 지원되는 암호 목록은 [SSL 오프로드](ssl-offload.html)를 참조하십시오.
