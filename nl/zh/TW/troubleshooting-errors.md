---

copyright:
  years: 2018
lastupdated: "2018-11-21"

keywords: error, message, troubleshooting, problems

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# 錯誤訊息疑難排解
{: #error-message-troubleshooting}

本主題提供您在建立/更新 {{site.data.keyword.loadbalancer_full}} 實例時可能遇到的一般錯誤訊息相關資訊。

| 錯誤 | 說明 | 解決方案 |
| ------------- | ------------- | ----- |
| `The maximum number of load balancers `n` has been reached.`| 每個帳戶只容許 50 個負載平衡器實例。| 請確定每個帳戶都有 50 個或更少的「負載平衡器」實例。|
| `The maximum number of given protocols `n` in load balancer product order has been reached.` | 佈建「負載平衡器」時，只能新增兩個通訊協定。| 如果您需要其他通訊協定，則在佈建之後，最多可以在「負載平衡器」管理流程的**通訊協定**標籤中新增十個。如需相關資訊，請參閱[監視及管理服務](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)。|
| `The maximum number of given server instances `n` in load balancer product order has been reached.` | 佈建「負載平衡器」時，只能新增十部伺服器。| 如果您需要其他伺服器，則在佈建之後，最多可以在「負載平衡器」管理流程的**伺服器實例**標籤中新增 50 部。如需相關資訊，請參閱[監視及管理服務](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)。|
| `Load balancer name must be a string and have at least 1 and up to 40 characters.` |「負載平衡器」名稱是必要項目。在名稱中，只能使用英數字元（或特殊字元 '-' 及 '.'）。名稱不得以特殊字元開頭或結尾，而且長度不能超過 40 個字元。| 輸入唯一的「負載平衡器」名稱。例如，"ui-servers" 或 "backend-servers"。|
| `Format error found in given load balancer name.` |「負載平衡器」名稱是必要項目。在名稱中，只能使用英數字元（或特殊字元 '-' 及 '.'）。名稱不得以特殊字元開頭或結尾，而且長度不能超過 40 個字元。| 輸入唯一的「負載平衡器」名稱。例如，"ui-servers" 或 "backend-servers"。|
| `Load balancer with the same name (case insensitive) already exists.` | 同名的負載平衡器已存在。| 輸入唯一的 Load Balancer 名稱，以繼續進行，例如，"ui-servers" 或 "backend-servers"。|
| `Load balancer description must be a string and not exceed 255 characters.` | Load Balancer 說明必須是字串，不得超過 255 個字元。| 說明限於 255 個字元。|
| `Frontend port 80 is already used.` | 您可能輸入了已在使用中的前端埠。| 輸入唯一的前端埠。|
| `Backend port must be an integer.` | 您可能輸入了無效的後端埠值。| 輸入後端埠號，介於 1 到 65535 之間。|
| `Since the protocol and port are not editable in health monitor, this error is impossible from UI.`| 您的專用子網路不是標準類型，且無法用來建立 Load Balancer。| 請與 IBM 支援中心聯絡。|
| `Private subnet `xyz` must have at least `n` free IP addresses.` | 選取的專用子網路沒有可用的 IP 位址。| 如需詳細資料，請檢查下列[疑難排解步驟](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting)。|
| `Specified private subnet VLAN is on router `xyz`. However, no public VLAN with `n` free IPs was found on the same router.` | 發生這種情況的原因是您已在佈建期間選取**使用此帳戶從公用子網路配置**選項。| 請改為選取**從 IBM 系統儲存區配置**，或與「IBM 支援中心」聯絡。|
| `Specified private subnet VLAN is on router `xyz`. However, no public subnet with `n` free IPs was found with VLAN on the same router.` | 發生這種情況的原因是您已在佈建期間選取**使用此帳戶從公用子網路配置**選項。| 請改為選取**從 IBM 系統儲存區配置**，或與「IBM 支援中心」聯絡。|
| `Given new description must be a string.`| 您可能輸入了無效的說明。| 請輸入 255 個字元以內的有效 Load Balancer 說明。|
| `A billing item is required to process a cancellation for load balancer uuid=aaaa-bbbb-cccc-dddd.` | 帳目資訊遺漏，或對您的帳戶而言無效，且 Load Balancer 無法取消。| 請與 IBM 支援中心聯絡。|
| `An internal error occurred. Data could not be retrieved.` | 無法擷取度量值資料 | 請重新載入頁面。如果問題仍然持續發生，請與 IBM 支援中心聯絡。|
| `Front-end port must be an integer between 1 and 65535 excluding the range 56500-56520.` | 您可能輸入了 56500-56520 之間的前端埠。| 請輸入唯一的埠號，介於 1 到 65535 之間，但排除 56500 到 56520 這個範圍。|
| `Back-end port must be an integer.` | 您可能輸入了無效的後端埠值。| 輸入後端埠號，介於 1 到 65535 之間。|
| `Back-end port must be an integer between 1 and 65535 excluding the range 56500-56520.` | 您可能輸入了介於 56500 與 56520 之間的後端埠。| 請輸入後端埠號，介於 1 到 65535 之間，但排除 56500 到 56520 這個範圍。|
| `Backend protocol HTTP is not compatible with frontend protocol TCP.` | 您可能選取了不相容的後端通訊協定與前端通訊協定組合。| 請選取有效的前端與後端通訊協定組合，格式為：`<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Member weight <some value> is provided for member abcd-xxxx-yyyy-2222. The allowed weight value is 0-100 `| 您可能輸入了無效的加權。| 請輸入加權值，介於 0 到 100 之間。|
| `There was a problem fetching the servers.` | 這可能是因為網路逾時問題所造成。| 請重新載入頁面。如果問題仍然持續發生，請與「IBM 支援中心」聯絡。|
