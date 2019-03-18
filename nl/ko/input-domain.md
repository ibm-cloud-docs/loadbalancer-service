---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 도메인 관련 정보 입력
보안 및 글로벌 로드 밸런싱이 제공될 도메인에 대한 정보를 입력합니다.

1. 시작하기 화면의 왼쪽에서 **개요**를 클릭하십시오. 도메인 이름(또는 하위 도메인 이름)을 입력하고 **도메인 추가**를 클릭하십시오. 
    
    <img src="images/Reliability3.png" alt="그림" style="width: 300px;"/>
    
    **참고:** IBM CIS(Cloud Internet Services)가 DNS 등록자가 아니므로 이 도메인(또는 하위 도메인)은 사전에 작성되어 있어야 합니다.

    서비스 세부사항 섹션 아래에서 새로 추가된 도메인은 초기에 보류 상태로 표시됩니다. 

    <img src="images/Reliability4.png" alt="그림" style="width: 300px;"/>    

2. 개별적인 DNS 등록자로 도메인에 대한 관리 페이지로 이동한 후에 NS 레코드를 정의하여 도메인/하위 도메인을 IBM 이름 서버에 위임하십시오.

DNS 데이터베이스에서 정보가 복제되려면 최대 24시간 정도 대기해야 할 수 있습니다. 일단 이 작업이 완료되면 도메인 상태가 활성으로 변경됩니다. 

<img src="images/Reliability5.png" alt="그림" style="width: 300px;"/>    
