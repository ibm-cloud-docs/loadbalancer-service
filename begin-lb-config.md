---



copyright:
  years: 2017, 2018
lastupdated: "2018-08-15"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Configure IBM Cloud Load Balancer parameters
Once you have created a load balancer, you can begin to configure it for elastic load balancing. Name your load balancer, and, optionally, add a description.

<img src="images/lb-config-basic.png" alt="drawing" style="width: 300px;"/>

Input the details of your application profile by identifying the protocols and ports your application is listening on. You Can use the same configuration for both front-end and back-end, or expose a different front-end port (for security purposes, for instance).

The default load balancing method is **Round Robin**. You may change it to Weighted **Round Robin** or **Least Connections** from the drop-down list depending on your application needs.

Optionally, you can enable **Session stickiness**, which is disabled by default. If enabled, then all requests from a given end-user (for example, one with the same source IP) go to the same backend server for a system-defined "sticky" time.

You Can also set the **Maximum connection limit** against your application.

Click **Add Protocol** to specify additional ports and protocols your application may be listening on. Be sure that all front-end ports are unique. You can choose HTTP, HTTPS or TCP as your front-end protocol.  

<img src="images/lb-add-protocol.png" alt="drawing" style="width: 300px;"/>

**NOTE**: A maximum of two ports may be defined at the time of initial configuration. Additional ports may be added later after the service instance is created.

The IBM Cloud Load Balancer terminates incoming HTTPS (HTTP over SSL) connections and communicates in plain-text HTTP with the back-end application servers, and offloads processor-intensive SSL tasks from your servers. You must upload your SSL Certificate. Select one of your available certificates from the drop-down list.  

<img src="images/lb-ssl-cert.png" alt="drawing" style="width: 300px;"/>

If you do not have an existing certificate, then click **Add a new Certificate**. This takes you to an IBM Cloud certificate service where you can either purchase a new certificate or upload an existing one. After adding the certificate, return to the load balancer configuration page and click the refresh icon below the SSL Certificate drop-down list to view and add your newly-uploaded certificate.

<img src="images/order-ssl-cert.png" alt="drawing" style="width: 300px;"/>

<img src="images/refresh-cert.png" alt="drawing" style="width: 300px;"/>

Click **Next**.

## Configure Health Checks
The health check definition is mandatory for each of your application ports. These are the back-end ports identified in the previous basic configuration menu.

<img src="images/config-health-check.png" alt="drawing" style="width: 300px;"/>

The system pre-populates a default health check configuration for these back-end ports. You may customize these settings to suit your application needs.

* **Interval**: Interval in seconds between two consecutive health check attempts
* **Timeout**: Maximum amount of time the system will wait for a response against a health check request
* **Max Trials**: Maximum number of additional health checks attempts the system will make prior to declaring a port unhealthy
* **Path**: The HTTP URL path for the health check     

Click **Next**.