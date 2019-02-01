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

# Setting Backend Encryption

Backend encryption is supported to allow end-to-end data traffic encryption. Not only is the traffic between the load balancer and the client encrypted, but so is the traffic between the load balancer and the backend server.

To enable backend encryption:

* If you are adding a new HTTPS protocol, set the frontend and backend to **HTTPS**.
* For existing HTTPS protocols, set the backend to **HTTPS**.
