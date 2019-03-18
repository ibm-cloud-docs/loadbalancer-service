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

# 계층 7 규칙
{: #layer-7-rules}

계층 7 규칙은 특정 값과 일치될 수신 트래픽의 일부를 정의합니다.

* 수신 트래픽이 지정된 규칙 값과 일치하면 규칙이 `true`로 평가됩니다.
* 계층 7 규칙은 항상 계층 7 정책과 연관됩니다. 다중 계층 7 규칙이 동일한 계층 7 정책과 연관될 수 있습니다.
* 다중 규칙이 정책과 연관된 경우 각 규칙이 `true` 또는 `false`로 평가됩니다. 
* 정책과 연관된 모든 규칙이 `true`로 평가되면 정책 조치가 요청에 적용됩니다. 그렇지 않으면 로드 밸런서가 다음 정책을 평가합니다.

규칙의 유형은 다음과 같습니다. 

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

다음은 규칙과 일치될 계층 7 트래픽의 일부를 나타냅니다.

유형      |추출되고 평가될 필드
----------| -----------------------
`HOST_NAME` |URL의 호스트 이름 파트(예: `api.my_company.com`)
`FILE_TYPE` |파일 유형을 나타내는 URL의 끝부분(예: `jpg`)
HEADER    |HTTP 헤더의 필드
COOKIE    |HTTP 헤더의 이름 지정된 쿠키 
PATH      |호스트 이름 다음에 오는 URL의 파트(예: `/index.html`)

또한 규칙에는 규칙이 평가되는 방법을 표시하는 비교 유형이 있습니다.
규칙의 비교 유형은 다음과 같습니다. 

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

비교 유형 |평가 유형
----------------|---------------------
`REGEX`           |추출된 필드(예: `hostname`)를 제공된 정규식과 일치
`STARTS_WITH`     |추출된 필드가 제공된 문자열로 시작되는지 여부 확인
`ENDS_WITH`       |추출된 필드가 제공된 문자열로 끝나는지 여부 확인
`CONTAINS`        |추출된 필드에 제공된 문자열이 포함되는지 여부 확인
`EQUAL_TO`        |추출된 필드가 제공된 문자열과 동일한지 여부 확인

**참고**: 모든 규칙 유형이 모든 비교 유형을 지원하지는 않습니다. 예를 들어, `FILE_TYPE`을 사용 중인 경우 비교 유형 `REGEX` 및 `ENDS_WITH`를 사용하는 것이 좋습니다.

## 계층 7 규칙 특성

특성  |설명
------------- | -------------
유형 |규칙의 유형을 지정합니다. 규칙 유형은 `HOST_NAME`(호스트 이름), `FILE_TYPE`(파일의 유형), `HEADER`(헤더), `COOKIE`(쿠키) 또는 `PATH`(경로)입니다.
비교 유형 |비교 유형은 규칙 유형, 키 및 값과 연관되어 규칙을 정의하고 트래픽을 분류하는 데 사용됩니다. 비교 유형은 `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS` 및 `EQUAL_TO`입니다.
키 |규칙 유형 `HEADER` 및 `COOKIE`에 대한 설명 키입니다. 
값 |규칙 유형 `HEADER` 및 `COOKIE`의 경우 값이 키와 비교됩니다.
반전 |이 값을 1로 설정하면 지정된 규칙이 일치하지 않을 때마다 이 L7 규칙 비교의 값이 `true`로 설정됩니다.
계층 7 정책 ID |규칙이 첨부되는 정책의 고유 ID입니다.
