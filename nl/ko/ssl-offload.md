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

# SSL 오프로드

모든 수신 HTTPS 연결의 경우, 로드 밸런서 서비스는 SSL 연결을 종료하고 백엔드 서버와 일반 텍스트 HTTP 통신을 설정합니다. CPU 집중 SSL 핸드쉐이크 및 암호화/복호화 태스크는 백엔드 서버로부터 전환되며, 애플리케이션 트래픽 처리를 위해 모든 자체 CPU 사이클의 사용이 허용됩니다. 

SSL 인증서는 로드 밸런서가 SSL 오프로드 태스크를 수행하는 데 필요합니다. 기존 SSL 인증서를 사용하거나 새 인증서를 구입할 수 있고 [IBM Cloud 인증서 저장소](https://control.softlayer.com/security/sslcerts)를 통해 SSL 인증서를 관리할 수 있습니다. 

# SSL 암호 스위트
로드 밸런서 서비스는 SSL 오프로드의 TLS 버전 1.2를 지원합니다.

다음의 SSL 암호가 로드 밸런서에 의해 지원됩니다.

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

로드 밸런서에 하나 이상의 HTTPS 프론트 엔드 애플리케이션 포트(프로토콜)가 구성된 경우, 기본적으로 위에서 사전 정의된 모든 SSL 암호가 로드 밸런서에 사용됩니다. 

**참고:** 필요한 경우 다른 SSL 암호를 로드 밸런서에 사용하도록 선택할 수 있습니다. 자세한 정보는 [HTTPS 애플리케이션에 대해 선호하는 암호 스위트 선택](custom-ciphers.html)을 참조하십시오.
