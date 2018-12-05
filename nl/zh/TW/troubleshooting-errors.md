---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 錯誤訊息疑難排解
本主題提供您在建立/更新 IBM Cloud Load Balancer 實例時可能遇到的一般錯誤訊息相關資訊。

| 錯誤 | 說明 | 解決方案 |
| ------------- | ------------- | ----- |
| `The maximum number of load balancers `n` has been reached.`| 每個帳戶只容許 50 個負載平衡器實例。| 請確定每個帳戶都有 50 個或更少的「負載平衡器」實例。|
| `The maximum number of given protocols `n` in load balancer product order has been reached.` | 佈建「負載平衡器」時，只能新增兩個通訊協定。| 如果您需要其他通訊協定，則在佈建之後，最多可以在「負載平衡器」管理流程的**通訊協定**標籤中新增十個。如需相關資訊，請參閱[監視及管理服務](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service)。|
| `The maximum number of given server instances `n` in load balancer product order has been reached.` | 佈建「負載平衡器」時，只能新增十部伺服器。| 如果您需要其他伺服器，則在佈建之後，最多可以在「負載平衡器」管理流程的**伺服器實例**標籤中新增 50 部。如需相關資訊，請參閱[監視及管理服務](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service)。|
| `Load balancer name must be a string and have at least 1 and up to 40 characters.` |「負載平衡器」名稱是必要項目。在名稱中，只能使用英數字元（或特殊字元 '-' 及 '.'）。名稱不得以特殊字元開頭或結尾，而且長度不能超過 40 個字元。| 輸入唯一的「負載平衡器」名稱。例如，"ui-servers" 或 "backend-servers"。|
| `Format error found in given load balancer name.` 「負載平衡器」名稱是必要項目。在名稱中，只能使用英數字元（或特殊字元 '-' 及 '.'）。名稱不得以特殊字元開頭或結尾，而且長度不能超過 40 個字元。| 輸入唯一的「負載平衡器」名稱。例如，"ui-servers" 或 "backend-servers"。|
| 同名的負載平衡器（不區分大小寫）已存在。| 同名的負載平衡器已存在。| 請輸入唯一的負載平衡器名稱，以繼續進行。例如 ui-servers、backend-servers 等。|
| 負載平衡器說明必須是字串，不得超過 255 個字元。| 負載平衡器說明必須是字串，不得超過 255 個字元。| 請輸入 255 個字元內有效的負載平衡器說明。|
| 前端埠 `80` 已被使用。| 您可能輸入了重複且已被使用的前端埠。| 請輸入唯一的前端埠。|
| 後端埠必須是整數。| 您可能輸入了無效的後端埠值。| 請輸入 1-65535 之間的有效後端埠。|
|因為在性能監視器中無法編輯通訊協定及埠，所以無法從使用者介面取得此錯誤。| 專用子網路 `xyz` 不是標準類型，因此無法用來建立負載平衡器。|請聯絡 IBM 支援中心。|
|專用子網路 `xyz` 必須至少有 `n` 個可用 IP 位址。|選取的專用子網路沒有可用的 IP 位址。|如需詳細資料，請檢查下列[疑難排解步驟](/docs/infrastructure/loadbalancer-service/troubleshooting-provisioning.html#insufficient-ip-addresses-in-your-subnet)。|
|指定的專用子網路 VLAN 位於路由器 `xyz`。不過，在同一個路由器上找不到具有 `n` 個可用 IP 的公用 VLAN。|發生這種情況的原因是您已在佈建期間選取「使用此帳戶從公用子網路配置」選項。|請選取「從 IBM 系統儲存區配置」選項，或聯絡 IBM 支援中心。|
|指定的專用子網路 VLAN 位於路由器 `xyz`。不過，在同一個路由器上找不到 VLAN 具有 `n` 個可用 IP 的公用子網路。|發生這種情況的原因是您已在佈建期間選取「使用此帳戶從公用子網路配置」選項。|請選取「從 IBM 系統儲存區配置」選項，或聯絡 IBM 支援中心。|
|給定的新說明必須是字串。|您可能輸入了無效的說明。| 請輸入 255 個字元內有效的負載平衡器說明。|
|需要有計費項目，才能處理取消負載平衡器 uuid=`aaaa-bbbb-cccc-dddd`。| |請聯絡 IBM 支援中心。|
|發生內部錯誤。無法擷取資料。|無法擷取度量值資料|請重新載入頁面。如果問題仍然持續發生，請聯絡 IBM 支援中心。|
|前端埠必須是 1 與 65535 之間的整數，但 56500-56520 範圍除外。|您可能輸入了 56500-56520 之間的前端埠。|請輸入 1-65535 之間的任何其他唯一埠，但 56500-56520 範圍除外。|
|後端埠必須是整數。| 您可能輸入了無效的後端埠值。| 請輸入 1-65535 之間的有效後端埠。|
|後端埠必須是 1 與 65535 之間的整數，但 56500-56520 範圍除外。|您可能輸入了 56500-56520 之間的後端埠。|請輸入 1-65535 之間的任何其他有效後端埠，但 56500-56520 範圍除外。|
|後端通訊協定 `HTTP` 與前端通訊協定 `TCP` 不相容。|您可能選取了不相容的後端通訊協定與前端通訊協定組合。|請選取有效的前端與後端通訊協定組合，如下所示：<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP|
|提供成員 `abcd-xxxx-yyyy-2222` 的成員權重 `<some value>`。容許的權重值為 0-100|您可能輸入了無效的權重。|請輸入 0-100 之間的權重。|
|提取伺服器時發生問題。|發生這種情況的原因可能是網路逾時問題。| 請重新載入頁面。如果問題仍然持續發生，請聯絡 IBM 支援中心。|
