---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 建立 IBM Cloud Load Balancer
若要建立 IBM Cloud Load Balancer 服務，請執行下列程序：

1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://control.softlayer.com/){: new_window} 並登入帳戶。

2. 按一下**型錄**，然後從「基礎架構」區段中導覽至**網路 > 負載平衡器**。

	<img src="images/catalog-load-balancer.png" alt="圖片" style="width: 600px;"/>

3. 選取 **IBM Cloud Load Balancer**（預設選項），然後按一下**建立**。 

	如果您看到**升級**，而非**建立**，則必須遵循[這些步驟 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/account/softlayerlink.html#link_customer_accounts) 來鏈結 IBM Cloud 基礎架構 (Softlayer) 帳戶。

	<img src="images/create-load-balancer.png" alt="圖片" style="width: 600px;"/>

4. 從**資料中心**下拉清單選取偏好的資料中心、檢閱資訊，然後按**下一步**。

	<img src="images/select-datacenter.png" alt="圖片" style="width: 600px;"/>

5. 指定負載平衡器類型。

	對於需要存取公用網際網路且面向網際網路的應用程式，請選取**公用（面向網際網路）**。

	<img src="images/select-lb-type.png" alt="圖片" style="width: 600px;"/>
	
	依預設，公用負載平衡器會從 IBM 全球位址儲存區收到一個全球唯一的公用 IP 位址。不過，如果您想要從自己的位址儲存區指派公用位址給它，或想要將它部署在帳戶內的防火牆服務後方，請檢查公用子網路是否具有[足夠的 IP 位址](troubleshooting-provisioning.html)，並選取**從帳戶中的公用子網路配置**。

	對於不需要存取公用網際網路且僅限內部使用的應用程式，請選擇**內部（專用）**類型。

	<img src="images/lb-type-private.png" alt="圖片" style="width: 500px;"/>

	對於面向網際網路及內部負載平衡器類型，都請在您想要部署負載平衡器的帳戶內挑選其中一個專用子網路。您的應用程式伺服器必須可從這個子網路進行存取。必要的話，請啟用 VLAN Spanning 來確保適當的網路連線功能。

	如果您看不到任何專用子網路，請按**前一步**，然後選取具有專用子網路的不同資料中心。

6. 按**下一步**，以完成配置。

## 下一步為何？
使用[基本參數](begin-lb-config.html)來配置您的負載平衡器。
