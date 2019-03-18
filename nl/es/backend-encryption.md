---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Configuración del cifrado de fondo
{: #setting-backend-encryption}

El cifrado de fondo permite el cifrado del tráfico de datos de extremo a extremo. No solo se trata del tráfico entre el equilibrador de carga el cliente cifrado, sino también del tráfico entre el equilibrador de carga y el servidor de fondo.

Para habilitar el cifrado de fondo:

* Si va a añadir un nuevo protocolo HTTPS, establezca el componente frontal y el programa de fondo en **HTTPS**.
* Para los protocolos HTTPS existentes, establezca el protocolo de fondo en **HTTPS**.
