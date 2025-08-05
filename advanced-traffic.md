---

copyright:
  years: 2017, 2025
lastupdated: "2025-08-05"

keywords: traffic, management, connection, persistence

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Advanced traffic management with IBM Cloud Load Balancer
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

Learn about the various advanced traffic-management features available with the {{site.data.keyword.loadbalancer_full}} service.
{: shortdesc}

## Max connections
{: #max-connections}

Use the `max connections` configuration to limit the maximum number of concurrent connections against a given front-end virtual port. The maximum concurrent connections against a given front-end virtual port or system-wide across all front-end virtual ports is `15000`. By default, it is set to the maximum value of `15000`.

## Session persistence
{: #session-persist}

The load balancer supports session persistence based on the source IP of the connection. As an example, if you have `source IP` type session persistence that is enabled for port `80` (HTTP), then subsequent HTTP connection attempts from the same source IP client are persistent on the same back-end server. This feature is available for all three supported protocols (HTTP, HTTPS, and TCP).

The load balancer also supports session persistence based on the HTTP Cookie. For example, if you have `HTTP Cookie` type session persistence that is enabled for port `80` (HTTP), when the load balancer receives its first response from the back-end server, it adds a cookie with the name `IBMCLB` and a value of `back-end server UUID` in the response header. All subsequent HTTP requests with this cookie that arrives at the load balancer are persistent on the same back-end server. This feature is available for both HTTP and HTTPS.

## HTTP keep alive
{: #http-keep-alive}

The load balancer supports `HTTP keep alive` when it is enabled on both the client and back-end servers. The load balancer attempts to reuse the server-side HTTP connections to increase connection efficiency and reduce latency.

## Connection timeouts
{: #connection-timeouts}

The following timeout values are used by the load balancer:

| Name | Description | Default timeout | User configurable |
| ------------------------------------------ | --------------------------------------------------- | ------------------- | ------------------- |
| Server-side connection attempt    | The maximum time window that the load balancer can use to establish a TCP connection with the back-end server. If the connection attempt is unsuccessful, the load balancer tries the next available server, according to the load-balancing method that you configured. | 5 seconds   | No   |
| Client-side idle connection  | The maximum idle time after which the load balancer brings down the client-side connection, if the client failed to close its connection properly.| 50 seconds  | Yes   |
| Server-side idle connection | The maximum idle time (with back-end protocol configuration of TCP) after which the load balancer closes the server-side connection. When HTTP is used as the back-end protocol, if the load balancer doesn't receive an HTTP response within the idle timeout period, it returns an error message to the client.                               | 50 seconds | Yes   |
{: caption="Load Balancer Timeout Values" caption-side="top"}

Server-side and client-side idle connection timeout values can be configured by using the API, cURL or from the CLI.

You can configure the server timeout (`ParameterName: serverTimeout`) and client timeout (`ParameterName: clientTimeout`) value in seconds up to 2 hours (Range: `1 - 7200` seconds) by using `UpdateLoadBalancerProtocols` method of `SoftLayer_Network_LBaaS_Listener` service. If you do not provide the server or client timeout values, the load balancer uses the default value (mentioned in the table) for the corresponding timeout.
{: note}



Setting long idle connection timeout values can cause your data path traffic to experience latencies or be blocked because the idle connections are counted toward the maximum concurrent connections of 15,000. Consider the idle connection timeout value along with the maximum number of concurrent connections to ensure that your data path traffic is not disrupted.
{: tip}

## Preserving end-client IP address
{: #preserving-end-client-ip-address}

IBM Cloud Load Balancer works as a reverse proxy, which handles incoming traffic from the client. It establishes a separate connection to the back-end server instance by using its own IP address. For HTTP connections with the back-end servers (against front-end HTTP or HTTPS connections), the load balancer preserves the original client IP address by including it inside the `X-Forwarded-For HTTP` header. For TCP connections, the original client IP information is not preserved.

## Preserving end-client protocol
{: #preserving-end-client-protocol}

IBM Cloud Load Balancer preserves the original protocol that is used by the client for front-end HTTP and HTTPS connections by including it inside the `X-Forwarded-Proto` HTTP header. This behavior does not apply to TCP protocols because the load balancer does not look at Layer-7 traffic when the TCP protocol is used.
