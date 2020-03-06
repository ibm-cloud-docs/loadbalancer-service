---

copyright:
  years: 2017, 2018
lastupdated: "2020-02-11"

keywords: traffic, management, connection, persistence

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Advanced traffic management with IBM Cloud Load Balancer
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

This section discusses several advanced traffic management features available with the {{site.data.keyword.loadbalancer_full}} service.

## Max connections
{: #max-connections}

Use the ‘max connections’ configuration to limit the maximum number of concurrent connections against a given front-end virtual port. By default, no limit is specified. The maximum possible concurrent connections against a given front-end virtual port or system-wide across all front-end virtual ports is 15000.  

## Session persistence
{: #session-persistence}

The load balancer supports session persistence based upon the source IP of the connection. As an example, if you have 'source IP' type session persistence enabled for port 80 (HTTP), then subsequent HTTP connection attempts from the same source IP client are persistent on the same back-end server. This feature is available for all three supported protocols (HTTP, HTTPS and TCP).

The load balancer also supports session persistence based upon the HTTP Cookie. For example, if you have 'HTTP Cookie' type session persistence enabled for port 80 (HTTP), when the load balancer receives its first response from the back-end server, it adds a cookie with the name `IBMCLB` and a value of `back-end server UUID` in the response header. All subsequent HTTP requests with this cookie arriving at the load balancer are persistent on the same back-end server. This feature is available for HTTP and HTTPS.

## HTTP keep alive
{: #http-keep-alive}
The load balancer supports 'HTTP keep alive' as long as it is enabled on both the client and back-end servers. The load balancer attempts to re-use the server-side HTTP connections to increase connection efficiency and reduce latency.

## Connection timeouts
{: #connection-timeouts}
The following timeout values are used by the load balancer:

| Name | Description | Default Timeout | User Configurable |                                                                                             
| ------------------------------------------ | --------------------------------------------------- | ------------------- | ------------------- |
| Server-side connection attempt    | The maximum time window that the load balancer can use to establish TCP connection with the back-end server. If the connection attempt is unsuccessful, the load balancer will try the next available server, according to the load balancing method you've configured. | 5 seconds   | NO   |
| Client-side idle connection  | The maximum idle time, after which the load balancer  brings down the client-side connection, if the client has failed to close its connection properly.| 50 seconds  | YES   |
| Server-side idle connection | The maximum idle time (with back-end protocol configuration of TCP), after which the load balancer closes the server-side connection. With the back-end protocol configuration of HTTP, if the load balancer fails to receive a response to its HTTP request within the idle timeout window, it will return an error message to the end-client.                                | 50 seconds | YES   |
{: caption="Table 1. Load Balancer Timeout Values" caption-side="top"}

Server-side & Client-side idle connection timeout value now can be configured using API. User can configure server timeout(ParameterName: serverTimeout) & client timeout(ParameterName: clientTimeout) value in seconds upto 2 hours (Range: 1 to 7200 seconds) using ‘UpdateLoadBalancerProtocols’ method of ‘SoftLayer_Network_LBaaS_Listener’ service.
If user does not provide the server or client timeout value, load balancer will use default value (mentioned in table) for the corresponding timeout.

## Preserving end-client IP address
{: #preserving-end-client-ip-address}

IBM Cloud Load Balancer works as a reverse proxy, which terminates incoming traffic from the client. It establishes a separate connection to the back-end server instance, using its own IP address. For HTTP connections with the backend servers (against front-end HTTP or HTTPS connections), the load balancer preserves the original client IP address by including it inside the `X-Forwarded-For HTTP` header. For TCP connections, the original client IP information is not preserved.

## Preserving end-client protocol
{: #preserving-end-client-protocol}
IBM Cloud Load Balancer preserves the original protocol used by the client for front-end HTTP and HTTPS connections. It does this by including it inside the `X-Forwarded-Proto` HTTP header. This does not apply to TCP protocols, since the load balancer does not look at Layer7 traffic when the TCP protocol is used.
