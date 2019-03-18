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

# 글로벌 로드 밸런서 구성 시작
글로벌 로드 밸런서 구성을 시작합니다.

1. **안정성** 섹션 아래에서 **글로벌 로드 밸런서**를 선택하십시오. 
    
    <img src="images/Reliability6.png" alt="그림" style="width: 300px;"/>

2. 상태 검사 섹션으로 화면을 하향 이동하십시오. 

   **참고:** 이 구성은 선택사항입니다. 사용자 정의 상태 검사를 정의하지 않으면 시스템에서 “/”를 기본 상태 검사 경로로 사용합니다. 

3. **상태 검사 작성** 단추를 클릭하여 사용자 정의 상태 검사를 정의하십시오.   

   상태 검사가 수행될 경로를 제공하십시오. 상태 검사에 HTTP 또는 HTTPS 프로토콜을 사용할 수 있습니다. 
   
4. **고급 옵션** 아래에서 상태 검사 간격, 재시도 횟수, 요청 방법 및 응답 본문 등의 기타 매개변수를 사용자 정의할 수 있습니다. 
   
   <img src="images/Reliability6.png" alt="그림" style="width: 300px;"/>
   
5. **리소스 프로비저닝**을 클릭하여 상태 검사 구성을 완료하십시오. 
