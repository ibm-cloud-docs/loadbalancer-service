---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Advanced Traffic Management with IBM Cloud Load Balancer
This section discusses several advanced traffic management features available with the load balancer service.

## Max Connections

Use the ‘max connections’ configuration to limit the maximum number of concurrent connections against a given front-end virtual port. By default, no limit is specified. The maximum possible concurrent connections against a given front-end virtual port or system-wide across all front-end virtual ports is 15000.  

## Session Persistence

The load balancer supports session persistence against a given VIP port based upon the `source IP` of the connection. As an example, if session persistence is enabled for port 80 (HTTP), then subsequent HTTP connection attempts from the same client (same source IP) are persistent on the same back-end server. This feature is available for all three supported protocols (HTTP, HTTPS and TCP).

The load balancer supports a maximum of 10,000 client persistence entries. The expiration time for these entries is 10 minutes. Additional requests received from the same client after 10 minutes may be forwarded to a different back-end server. If the session persistence entry has not expired, but the back-end port has become unhealthy, a new server is selected for forwarding any subsequent client connections.  

## HTTP Keep Alive
The load balancer supports `HTTP keep alive` as long as it is enabled on both the client and back-end servers. The load balancer attempts to re-use the server-side HTTP connections to increase connection efficiency and reduce latency.

## Connection Timeouts
The following timeout values are used by the load balancer. These values cannot be customized at this time.

| Name | Description | Timeout |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
| Server-side connection attempt    | The maximum time window that the load balancer can use to establish TCP connection with the back-end server. If the connection attempt is unsuccessful, the load balancer will try the next available server, according to the load balancing method you've configured. | 5 seconds   |
| Client-side idle connection  | The maximum idle time, after which the load balancer  brings down the client-side connection, if the client has failed to close its connection properly.| 50 seconds  |
| Server-side idle connection | The maximum idle time (with back-end protocol configuration of TCP), after which the load balancer closes the server-side connection. With the back-end protocol configuration of HTTP, if the load balancer fails to receive a response to its HTTP request within the idle timeout window, it will return an error message to the end-client.                                | 50 seconds |
{: caption="Table 1. Load Balancer Timeout Values" caption-side="top"} 

## Preserving end-client IP address 

The load balancer works as a reverse proxy, which terminates incoming traffic from the client. It establishes a separate connection to the back-end server instance, using its own IP address. For HTTP connections with the backend servers (against front-end HTTP or HTTPS connections), the load balancer preserves the original client IP address by including it inside the `X-Forwarded-For HTTP` header. For TCP connections, the original client IP information is not preserved.