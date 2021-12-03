---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: health check, http, tcp, ports

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Performing health checks
{: #performing-health-checks-with-ibm-cloud-load-balancer}
{: help}
{: support}

The load balancer conducts periodic health checks to monitor the health of the back-end ports and forwards client traffic to them. If a given back-end server port is found unhealthy, then new connections are not forwarded to it. The load balancer continues to monitor the health of these unhealthy ports, and resumes their use if they are found healthy again by successfully passing two consecutive health check attempts.
{: shortdesc}

Health check definitions are mandatory for each of the back-end application ports. The port and protocol under health check configuration must match with the defined back-end port and protocol; otherwise, the configuration is rejected.

The health checks against HTTP，HTTPS and TCP ports are conducted as follows:

* **HTTP** - An `HTTP GET` request against a pre-specified URL is sent to the back-end server port. The server port is marked healthy upon receiving a `200 OK` response. The default `GET` URL is “/” via the GUI, and it can be customized.

* **HTTPS** - Only applicable when back-end encryption is enabled and the back-end protocol is set to HTTPS. The mechanism is the same as **HTTP**, except that all health check messages are SSL encrypted. For more information, see [Setting back-end encryption](/docs/loadbalancer-service?topic=loadbalancer-service-setting-backend-encryption).

* **TCP** - The load balancer attempts to open a TCP connection with the back-end server on a specified TCP port. The server port is marked healthy if the connection attempt is successful. Then, the connection is closed.

   The default health check interval is 5 seconds. The default timeout against a health check request is 2 seconds, and the default number of retry attempts is 2.
   {: note}
