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

# Resolución de problemas de la expansión de VLAN del equilibrador de carga
{: #load-balancer-vlan-spanning-troubleshooting}

En este tema se proporciona información sobre los problemas comunes que puede encontrar cuando el equilibrador de carga y las instancias de cálculo conectadas al equilibrador de carga están en distintas subredes. La expansión de VLAN debe estar habilitada para que el equilibrador de carga se comunique y reenvíe las solicitudes a las instancias de cálculo que residan en otra subred.

1. Inicie la sesión en el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com){:new_window}, vaya a **Red > Gestión de IP** y luego pulse **VLAN**.

2. Cambie **Expansión de VLAN** por **Activado**.

<img src="images/vlan-spanning.png" alt="dibujo" style="width: 500px;"/>

Esto abre la comunicación entre el equilibrador de carga y sus instancias de cálculo.
