---

copyright:
  years: 2018
lastupdated: "2018-11-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Error Message Troubleshooting
This topic provides information on common error messages you may encounter while creating/updating an instance of IBM© Cloud Load Balancer.

| Error | Explanation  | Solution  |
| ------------- | ------------- | ----- |
| `The maximum number of load balancers `n` has been reached.`| We only allow 50 load balancer instances per account. | Ensure you have 50 or less Load Balancer instances per account. |
| `The maximum number of given protocols `n` in load balancer product order has been reached.` | Only two protocols can be added while provisioning a Load Balancer.  | If you need more protocols, then after provisioning, you can add up to ten from the **Protocols** tab in the Load Balancer management flow. For more information, refer to [monitoring and managing your service](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `The maximum number of given server instances `n` in load balancer product order has been reached.` | Only ten servers can be added while provisioning a Load Balancer. | If you need additional servers, then after provisioning, you can add up to 50 from the **Server Instances** tab in the Load Balancer management flow. For more information, refer to [monitoring and managing your service](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Load balancer name must be a string and have at least 1 and up to 40 characters.` | The Load Balancer name is mandatory. Use only alphanumeric characters (or special characters '-' and '.') for the name. The name must not begin or end with a special character, and must be limited to 40 characters in length. | Enter a unique Load Balancer name. For example, "ui-servers" or  "backend-servers".|
| `Format error found in given load balancer name.` | The Load Balancer name is mandatory. Use only alphanumeric characters (or special characters '-' and '.') for the name. The name must not begin or end with a special character, and must be limited to 40 characters in length. | Enter a unique Load Balancer name. For example, "ui-servers" or "backend-servers".|
| `Load balancer with the same name (case insensitive) already exists.` | A load balancer with the same name exists. | Enter a unique Load Balancer name to proceed further, for example, "ui-servers" or "backend-servers". |
| `Load balancer description must be a string and not exceed 255 characters.` | The Load Balancer description must be a string that does not exceed 255 characters. | Limit the description to 255 characters. |
| `Frontend port 80 is already used.` | You may have entered a front end port that is already in use. | Enter a unique front end port. |
| `Backend port must be an integer.` | You may have entered an invalid back-end port value. | Enter a back-end port number between 1 and 65535. |
| `Since the protocol and port are not editable in health monitor, this error is impossible from UI.`| Your private subnet is not a standard type and cannot be used to create the Load Balancer. | Contact IBM support. |
| `Private subnet `xyz` must have at least `n` free IP addresses.` | The selected private subnet does not have any free IP addresses. | Please check these [troubleshooting steps](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting) for more information. |
| `Specified private subnet VLAN is on router `xyz`. However, no public VLAN with `n` free IPs was found on the same router.` | This happens because you selected the **Allocate from public subnet from this account** option during provisioning. | Select **Allocate from IBM System Pool** instead or contact IBM Support.|
| `Specified private subnet VLAN is on router `xyz`. However, no public subnet with `n` free IPs was found with VLAN on the same router.` | This happens because you selected the **Allocate from public subnet from this account** option during provisioning. | Select **Allocate from IBM System Pool** instead or contact IBM Support.|
| `Given new description must be a string.`| You may have entered an invalid description. | Enter a valid Load Balancer description, no larger than 255 characters. |
| `A billing item is required to process a cancellation for load balancer uuid=aaaa-bbbb-cccc-dddd.` | Billing information is missing or invalid for your account, and the Load Balancer cannot be cancelled. | Contact IBM support.|
| `An internal error occurred. Data could not be retrieved.` | Metrics data cannot be retrieved | Reload the page. If the issue still persists, then contact IBM support. |
| `Front-end port must be an integer between 1 and 65535 excluding the range 56500-56520.` | You may have entered a front-end port number between 56500-56520. | Enter a unique port number between 1 to 65535, but excluding the range of 56500 to 56520. |
| `Back-end port must be an integer.` | You may have entered an invalid back-end port value. | Enter a back-end port number between 1 and 65535. |
| `Back-end port must be an integer between 1 and 65535 excluding the range 56500-56520.` | You may have entered a back-end port between 56500 and 56520.| Enter a back-end port number between 1 and 65535, but excluding the range of 56500 to 56520. |
| `Backend protocol HTTP is not compatible with frontend protocol TCP.` | You may have selected an incompatible back-end protocol and front-end protocol combination. | Select a valid front-end and back-end protocol combination, in the form: `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Member weight <some value> is provided for member abcd-xxxx-yyyy-2222. The allowed weight value is 0-100 `| You may have entered an invalid weight. | Enter a weight value between 0 and 100. |
| `There was a problem fetching the servers.` | This can happen as a result of network timeout issues. | Reload the page. If issue still persists, contact IBM Support.|