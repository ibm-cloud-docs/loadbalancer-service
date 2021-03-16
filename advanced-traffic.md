---

copyright:
  years: 2017, 2021
lastupdated: "2021-03-10"

keywords: traffic, management, connection, persistence

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:term: .term}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:table: .aria-labeledby="caption"}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Advanced traffic management with IBM Cloud Load Balancer
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

Learn about several advanced traffic management features available with the {{site.data.keyword.loadbalancer_full}} service.
{:shortdesc}

## Max connections
{: #max-connections}

Use the `max connections` configuration to limit the maximum number of concurrent connections against a given front-end virtual port. The maximum possible concurrent connections against a given front-end virtual port or system-wide across all front-end virtual ports is 15000. By default, it is set to the maximum value of 15000.

## Session persistence
{: #session-persist}

The load balancer supports session persistence based on the source IP of the connection. As an example, if you have `source IP` type session persistence that is enabled for port 80 (HTTP), then subsequent HTTP connection attempts from the same source IP client are persistent on the same back-end server. This feature is available for all three supported protocols (HTTP, HTTPS, and TCP).

The load balancer also supports session persistence based upon the HTTP Cookie. For example, if you have `HTTP Cookie` type session persistence enabled for port 80 (HTTP), when the load balancer receives its first response from the back-end server, it adds a cookie with the name `IBMCLB` and a value of `back-end server UUID` in the response header. All subsequent HTTP requests with this cookie arriving at the load balancer are persistent on the same back-end server. This feature is available for HTTP and HTTPS.

## HTTP keep alive
{: #http-keep-alive}
The load balancer supports `HTTP keep alive` as long as it is enabled on both the client and back-end servers. The load balancer attempts to reuse the server-side HTTP connections to increase connection efficiency and reduce latency.

## Connection timeouts
{: #connection-timeouts}
The following timeout values are used by the load balancer:

| Name | Description | Default timeout | User configurable |                                                                                             
| ------------------------------------------ | --------------------------------------------------- | ------------------- | ------------------- |
| Server-side connection attempt    | The maximum time window that the load balancer can use to establish TCP connection with the back-end server. If the connection attempt is unsuccessful, the load balancer tries the next available server, according to the load-balancing method that you configured. | 5 seconds   | No   |
| Client-side idle connection  | The maximum idle time after which the load balancer brings down the client-side connection, if the client failed to close its connection properly.| 50 seconds  | Yes   |
| Server-side idle connection | The maximum idle time (with back-end protocol configuration of TCP) after which the load balancer closes the server-side connection. With the back-end protocol configuration of HTTP, if the load balancer fails to receive a response to its HTTP request within the idle timeout window, it returns an error message to the end-client.                                | 50 seconds | Yes   |
{: caption="Table 1. Load Balancer Timeout Values" caption-side="top"}

Server-side and client-side idle connection timeout value can be configured by using API. You can configure the server timeout(ParameterName: serverTimeout) and client timeout(ParameterName: clientTimeout) value in seconds up to 2 hours (Range: 1 - 7200 seconds) using `UpdateLoadBalancerProtocols` method of `SoftLayer_Network_LBaaS_Listener` service.
If you do not provide the server or client timeout value, the load balancer uses default value (mentioned in the table) for the corresponding timeout.

Setting long idle connection timeout values can cause your data path traffic to experience latencies or be blocked because the idle connections are counted towards the maximum concurrent connections of 15,000. Consider idle connection timeout value along with the maximum number of concurrent connections to ensure your data path traffic is not disrupted.
{: tip}

## Preserving end-client IP address
{: #preserving-end-client-ip-address}

IBM Cloud Load Balancer works as a reverse proxy, which terminates incoming traffic from the client. It establishes a separate connection to the back-end server instance by using its own IP address. For HTTP connections with the back-end servers (against front-end HTTP or HTTPS connections), the load balancer preserves the original client IP address by including it inside the `X-Forwarded-For HTTP` header. For TCP connections, the original client IP information is not preserved.

## Preserving end-client protocol
{: #preserving-end-client-protocol}
IBM Cloud Load Balancer preserves the original protocol that is used by the client for front-end HTTP and HTTPS connections. It does this by including it inside the `X-Forwarded-Proto` HTTP header. This does not apply to TCP protocols because the load balancer does not look at Layer-7 traffic when the TCP protocol is used.
